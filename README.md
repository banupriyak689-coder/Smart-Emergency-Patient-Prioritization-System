# Smart Emergency Patient Prioritization System

A beginner-friendly academic project using **Java 17, Spring Boot, Maven, HTML, CSS, and JavaScript**.

## Features
- Patient registration with ID, name, age, urgency, and notes
- Java backend REST API
- Automatic priority sorting: Critical → High → Medium → Low
- Dashboard totals for critical, high, and other patients
- Remove an individual patient from the queue
- Responsive hospital dashboard UI

## Requirements
- JDK 17 or newer
- Apache Maven 3.6+ installed
- VS Code (recommended) or another code editor

Check installations in a terminal:
```bash
java -version
mvn -version
```

## Run the project
1. Extract this ZIP.
2. Open the **SmartEmergencySystem** folder in VS Code (the folder containing `pom.xml`).
3. Open **Terminal → New Terminal**.
4. Run:
   ```bash
   mvn spring-boot:run
   ```
5. Wait until the terminal shows that Spring Boot has started.
6. Open this URL in your browser: **http://localhost:8080**
7. Register a few sample patients with different urgency levels. Critical patients should appear first.

**Important:** Open `http://localhost:8080` while the Java server is running. Do not open `index.html` directly or use Live Server for this integrated version, because the page calls the Java API.

## API endpoints
| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/patients` | List patients, highest urgency first |
| `POST` | `/api/patients` | Register a patient |
| `DELETE` | `/api/patients/{id}` | Remove a particular patient |
| `DELETE` | `/api/patients/next` | Remove the highest-priority patient |
| `GET` | `/api/patients/count` | Get current patient count |

Example POST JSON:
```json
{
  "id": "P101",
  "name": "Sample Patient",
  "age": 35,
  "priority": 4,
  "symptoms": "Example notes"
}
```

Urgency values: `4 = Critical`, `3 = High`, `2 = Medium`, `1 = Low`.

## Upload to GitHub
1. Create a repository on GitHub, for example `SmartEmergencySystem`.
2. Extract the ZIP and open the project folder.
3. In VS Code Source Control, choose **Initialize Repository**.
4. Stage files, enter a commit message such as `Initial project`, and commit.
5. Choose **Publish to GitHub** and follow the prompts.

You can also use Git commands from the project folder:
```bash
git init
git add .
git commit -m "Initial Smart Emergency System project"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/SmartEmergencySystem.git
git push -u origin main
```
Replace the URL with your own repository URL.

## Important limitations
- This demo keeps patients in server memory. The list resets when the Java application restarts.
- It is an academic simulation, not a real clinical triage tool. Do not use it to make real medical decisions.
- This version uses Java's built-in `PriorityQueue`; it does not include a persistent database or a manually coded Max-Heap.
