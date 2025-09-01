# Artifact Repository Manager with Nexus

Nexus supports many types of artifacts like **Docker images**, **npm packages**, **Maven packages**, etc.  
This makes it a great choice for an artifact repository. It is also easy to set up and use.

⚠️ The downside of Nexus is that it can get **messy quickly** because of its wide range of features.

👉 **Recommendation**: Use Nexus mainly for storing **Docker images**, **Composer (PHP)**, and **Maven packages**.

---

## Nexus as a Proxy

Nexus can act as a **proxy for external repositories** such as **npmjs**, **Maven Central**, etc.

- When you pull a package from an external repository, Nexus caches it inside your repository.
- This way, your Nexus instance acts as a **local cache**, improving reliability and performance.

---

## Nexus REST API

Nexus provides a REST API that can be used to **push and pull artifacts**, enabling automation of CI/CD pipelines.

### Examples

- **List all repositories**
  ```bash
  curl -u user:pwd -X GET 'http://{host}:8081/service/rest/v1/repositories'
  ```


List all components in a specific repository
```bash
curl -u user:pwd -X GET 'http://{host(ip}:8081/service/rest/v1/components?repository=<INSERT_REPO>'

curl -u user:pwd -X GET 'http://{host(ip)}:8081/service/rest/v1/components/<ID>'

```

# Multi-Tenancy & Access Control

- Nexus supports **multi-tenancy**, meaning you can create multiple repositories for different users/teams.  
- Access can be **restricted using roles and users**, ensuring security and separation of responsibilities.

---

# Running Nexus in Containers

- Nexus can run inside a **Docker container**.  
- This makes it easy to run Nexus inside a **Kubernetes cluster** for scalability and portability.
