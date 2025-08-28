# Artifacts, Artifactory & Docker (Beginner Notes)

## What is an Artifact?
- An **artifact** is a file produced by a build process.
- It’s the "output" of your code that can be deployed or reused.
- Examples: `.jar`, `.war`, `.zip`, Docker image.

👉 Example: A Java project builds a `.jar` file.

---

## What is inside a JAR file?
- A JAR is basically a **ZIP file** with:
  - Compiled `.class` files
  - Resources (configs, images, etc.)
  - A `META-INF/MANIFEST.MF` file (main class & other info)

⚠️ Note: In Maven, `pom.xml` is **NOT** the manifest.
- `pom.xml` = project dependencies & build config
- `MANIFEST.MF` = info on how to run the JAR

---

## What is an Artifactory?
- An **Artifactory** is a repository that stores **artifacts**.
- Examples: Nexus, JFrog Artifactory.
- Uses:
  - Store build outputs (jars, wars, Docker images, etc.)
  - Host dependencies for faster & reliable builds
  - Keep version history of builds

---

## Why Docker?
- Without Docker → many artifacts, works differently on each system.
- With Docker → one image works everywhere.

Benefits:
- Consistency → "If it works in Docker, it works anywhere."
- Same image for Dev, Test, and Prod
- Faster deployment
- Fewer artifact types to manage
