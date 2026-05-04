## 🚀 How to Use

This project adopts a **centralized build and dependency management approach** using a Parent POM and a BOM (Bill of Materials). Follow the steps below to integrate it into your own projects.

### 1. Inherit the Platform Parent POM

Ensure your project inherits the shared build configuration:

```xml
<parent>
    <groupId>com.leumanuel.aggregator</groupId>
    <artifactId>bigdata-build</artifactId>
    <version>1.0.3</version>
    <relativePath/> <!-- lookup remote -->
</parent>
```
### 2. Configure the Maven Repository
Add the GitHub Packages repository where the artifacts are hosted:

```xml
<repositories>
    <repository>
        <id>github</id>
        <url>https://maven.pkg.github.com/Leupesquisa/bigdata-aggregator/</url>
    </repository>
</repositories>
```

### 3. Import the BOM (Bill of Materials)
Use the BOM to manage dependency versions consistently:

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.leumanuel.aggregator</groupId>
            <artifactId>bigdata-bom</artifactId>
            <version>1.0.3</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

### 4. Configure Your Project Parent
Each module or service should inherit from your own project parent POM:

```xml
<parent>
    <groupId>your.group.id</groupId>
    <artifactId>your-parent-artifact</artifactId>
    <version>your-version</version>
</parent>
```

This keeps your internal project structure flexible while still leveraging the shared platform.

### 💡 Best Practices
Avoid manual versions: Do not specify dependency versions manually — rely on the BOM.

Hierarchy: Maintain a clean parent hierarchy.

Alignment: Keep versions aligned across all modules.

Auth: Configure authentication for GitHub Packages in your settings.xml if required.

### 📦 Benefits
Centralized management: Single point of control for dependencies.

Consistency: Predictable builds across different projects.

Maintenance: Easier upgrades and maintenance.

Scalability: Scalable multi-module architecture.
