# GridDocker

A **Maven-based Selenium automation framework** with support for **Selenium Grid (Docker Compose)**.
Ready to open in **VS Code** or **Eclipse** and run tests locally or on a containerized Selenium Grid.

---

## Project details

* **Group ID:** `com.w2a`
* **Artifact ID:** `GridDocker`
* **Version:** `0.0.1-SNAPSHOT`
* **Build tool:** Apache Maven
* **Main dependency:** `selenium-java:2.53.1`

---

## Prerequisites

* Java JDK 8 or higher
* Apache Maven
* Git (optional, for version control)
* Docker & Docker Compose (for Selenium Grid)
* IDE: VS Code (with Java & Maven extensions) or Eclipse

---

## Quick start

### 1. Clone or extract

```bash
# Clone from Git (replace URL with your repo)
git clone https://github.com/<your-username>/GridDocker.git
cd GridDocker

# OR if you have GridDocker.zip: extract and cd into the folder
```

### 2. Open project

* VS Code: `code .`
  — Install **Java Extension Pack** and **Maven for Java** if prompted.
* Eclipse: File → Import → **Existing Maven Projects** → select project root.

### 3. Build

```bash
mvn clean install
```

### 4. Run tests

```bash
mvn test
```

---

## Run with Docker Compose (Selenium Grid)

If you want distributed browser execution, use the included `docker-compose.yml`.

### Start Grid

```bash
docker-compose up -d
```

This should start the Selenium Hub and browser nodes (Chrome/Firefox). Hub typically available at `http://localhost:4444`.

### Stop Grid

```bash
docker-compose down
```

### Configure tests to use Grid

In your Java test setup, point `RemoteWebDriver` to the hub:

```java
import org.openqa.selenium.remote.RemoteWebDriver;
import org.openqa.selenium.remote.DesiredCapabilities;
import java.net.URL;

DesiredCapabilities caps = DesiredCapabilities.chrome(); // or firefox()
RemoteWebDriver driver = new RemoteWebDriver(new URL("http://localhost:4444/wd/hub"), caps);
```

---

## Recommended project structure

```
GridDocker/
│── pom.xml
│── .project
│── docker-compose.yml
│── src/
│   ├── main/java/     # application code (if any)
│   └── test/java/     # selenium test classes
```

---

## VS Code tips

* Create a file `README.md` in project root and paste this content.
* Open integrated terminal with **Ctrl+\`** to run Maven commands.
* Preview Markdown with **Ctrl+Shift+V** (or Cmd+Shift+V on Mac).

---

## Git (optional)

Initialize and push:

```bash
git init
git add .
git commit -m "Initial commit — add project and README"
git branch -M main
git remote add origin https://github.com/<your-username>/GridDocker.git
git push -u origin main
```

---

## Notes & next steps

* Selenium version `2.53.1` is old; consider upgrading to a newer Selenium (3.x/4.x) for better browser support.
* If you want, I can add:

  * a ready-to-run `SampleTest.java` under `src/test/java`
  * a `.gitignore`
  * GitHub badges for the README

---

## License

MIT — use and modify freely.
