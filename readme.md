A ready-to-use **Spring Boot starter project** for uploading, serving, deleting, and retrieving metadata of files.
Comes with a **Postman collection** for easy testing.

This project is ideal for developers who want a clean **file management boilerplate** to integrate into larger applications such as:

* Document storage systems
* Media servers
* Student projects & demos
* Freelance projects where file handling is required

> [Deploy a Spring Boot File Server on a Free VPS (Step-by-Step Guide)](https://dev.to/boiler_agents/deploy-your-own-production-grade-file-server-on-a-vps-for-free-in-just-a-few-steps-4f7a)

---

## 🚀 Features

* Upload files via REST API
* Stream or download files with correct MIME type
* Delete files by name
* List all uploaded files
* Retrieve file metadata (size, type, last modified)
* Includes Postman collection for testing

---

## 🛠️ Tech Stack

* Java 21
* Spring Boot 3.5.4
* Maven

---

## ⚙️ Setup Instructions

### 1. Prerequisites

* Install **Java 21+**
* Install **Maven**
* Install an IDE (Eclipse, IntelliJ IDEA, or VS Code with Java plugin)

### 2. Unzip & Open Project

1. After purchase, download the provided ZIP file.
2. Extract/unzip it to a folder, e.g.:

   ```
   C:/projects/springboot-file-upload-api
   ```
3. Open this folder as a **Maven project** in your IDE.

### 3. Update Configuration

Edit the file `src/main/resources/application.properties` according to your needs:

```properties
# Server Configuration
spring.application.name=springboot-file-upload-api
server.port=8000

# File Configuration
spring.servlet.multipart.max-file-size=50MB
spring.servlet.multipart.max-request-size=50MB

# Change this path to where you want files to be stored
upload.path=D://test-file-upload-folder
```

👉 The directory is automatically created upon first use if it's not already present.

### 4. Run the Project

Run the application using Maven:

```bash
mvn spring-boot:run
```

Or directly from your IDE → **Run as → Spring Boot App**.

The server starts at:

```
http://localhost:8000
```

---

## 📡 API Endpoints

### 🔼 Upload File

**POST** `/file` – Uploads a file to the server. Returns a unique filename.

**Body (form-data):**

* `file` → (binary file)

Example:

```bash
curl -F "file=@logo.png" http://localhost:8000/file
```

---

### 📥 Stream/Download File

**GET** `/file/{filename}` – Streams or downloads the file.

Example:

```
http://localhost:8000/file/3eff281d-5e2a-4b54-b59f-b579073c0253.png
```

---

### ❌ Delete File

**DELETE** `/file/{filename}` – Deletes a file permanently.

Example:

```
http://localhost:8000/file/0e149ac6-936d-4fbb-8e7f-8156913c3a72.jpg
```

---

### 📃 List All Files

**GET** `/file/list` – Returns all uploaded files.

Example Response:

```json
[
  "3eff281d-5e2a-4b54-b59f-b579073c0253.png",
  "0e149ac6-936d-4fbb-8e7f-8156913c3a72.jpg",
  "622c5d89-03fc-4dea-93ad-7fcc69eb49eb.mp4"
]
```

---

### ℹ️ Get File Info

**GET** `/file/info/{filename}` – Retrieves file metadata.

Example Response:

```json
{
  "name": "622c5d89-03fc-4dea-93ad-7fcc69eb49eb.mp4",
  "size": "12.5MB",
  "mimeType": "video/mp4",
  "lastModified": "2025-08-23T15:42:00"
}
```

---

## 📬 Postman Collection

A ready-made Postman collection is included (`file-upload-api.postman_collection.json`).
Simply **import into Postman** and start testing the APIs.

---

## 🔒 Notes

* Authentication is **not included** (can be added with Spring Security).
* File storage location is configurable via `application.properties`.
* Files are stored locally in the folder you set in `upload.path`.

---

## 📜 License

This project is licensed under the **MIT License** – you can use it in personal and commercial projects.

---

## 🎯 Who is this for?

* Java/Spring Boot developers who want a quick boilerplate.
* Students working on projects that require file handling.
* Freelancers who need ready-made file upload APIs for client work.
---

## About Boileragents

Boileragents builds practical, ready-to-use boilerplates so you can skip the boring setup and start coding.

* GitHub: [https://github.com/boileragents](https://github.com/boileragents)
* dev.to: [https://dev.to/boiler_agents](https://dev.to/boiler_agents)
* Email: [boileragents@gmail.com](mailto:boileragents@gmail.com)

---

## If you found this boilerplate useful, you might also like it's pro-version:

- [FiloraFS – Easy & Secure File Storage System for Developers](https://boileragent.gumroad.com/l/filorafs-file-storage-system)  
  *Secure login, role-based access, AWS S3 file storage service in minutes.*

---

- If this boilerplate saved you time, give it a ⭐ on GitHub and share your feedback.
- Need a custom feature? Reach out at `boileragents@gmail.com`.
- 👉 Subscribe to get updates on new boilerplates, free resources, and practical tips — [https://boileragent.gumroad.com/](https://boileragent.gumroad.com/)
