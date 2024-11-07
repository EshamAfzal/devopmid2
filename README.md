
### **README.md**

```markdown
# Personal Portfolio Project

This project is a personal portfolio website developed by **Esham Afzal** (Student ID: 221008). It showcases basic frontend development skills, including HTML and CSS. The website is containerized using Docker and served through an Nginx server.

## Project Overview

This portfolio website contains the following sections:
- **Home**: Introduction and overview of the developer.
- **About**: Information about the developer.
- **Services**: A brief list of services offered.
- **Contact Us**: A link to a registration page (for demonstration).

The project is containerized using Docker and served through an Nginx web server.

## Git Workflow

The project follows a Git branching strategy to manage development and deployment:
1. **Main Branch** (`main`): Contains stable, production-ready code.
2. **Develop Branch** (`develop`): Active development branch.
3. **Feature Branches**: Individual features are developed on separate branches. Example:
   - `feature/frontend`: Contains the frontend-related changes (HTML, CSS).

### Git Commands Used

- **Initialize the repository and set up remote:**
  ```bash
  git init
  git remote add origin https://github.com/<friend-github-username>/<repository-name>.git
  git push -u origin main
  ```

- **Create and push the `develop` branch:**
  ```bash
  git checkout -b develop
  git push -u origin develop
  ```

- **Create and push a `feature/frontend` branch:**
  ```bash
  git checkout -b feature/frontend
  git add index.html style.css
  git commit -m "Add frontend files"
  git push origin feature/frontend
  ```

- **Merge feature branch into `develop`:**
  ```bash
  git checkout develop
  git merge feature/frontend
  git push origin develop
  ```

- **Create a pull request** from `develop` to `main` on GitHub to simulate the review process.

## Docker Setup

### Dockerfile

The Dockerfile is used to build a Docker image to serve the frontend of the website using Nginx.

```Dockerfile
# Step 1: Use the official Nginx image from Docker Hub
FROM nginx:latest

# Step 2: Set the working directory inside the container
WORKDIR /usr/share/nginx/html

# Step 3: Copy the static files from the local directory to the container's Nginx HTML directory
COPY . .

# Step 4: Expose port 80 to access the site via the browser
EXPOSE 80

# Step 5: Run Nginx in the foreground (default command for Nginx)
CMD ["nginx", "-g", "daemon off;"]
```

### docker-compose.yml

The `docker-compose.yml` file is used to simplify the process of building and running the Docker container for this project.

```yaml
version: '3.8'

services:
  frontend:
    build: .
    container_name: frontend-container
    ports:
      - "8080:80"  # Exposes the container’s port 80 to the host’s port 8080
    volumes:
      - .:/usr/share/nginx/html  # Mount the local directory to the container’s web root
    networks:
      - frontend-network

networks:
  frontend-network:
    driver: bridge
```

### .env File

If required, environment variables (e.g., database configurations) can be added in the `.env` file. For now, there are no specific environment variables needed for the frontend part.

```plaintext
# Example environment variables (if needed in the future)
POSTGRES_USER=your_database_user
POSTGRES_PASSWORD=your_database_password
POSTGRES_DB=your_database_name
```

Make sure to **add `.env` to `.gitignore`** to avoid pushing sensitive data to GitHub.



## Running the Project Locally with Docker Compose

To get the project running on your local machine, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/<friend-github-username>/<repository-name>.git
   cd <repository-name>
   ```

2. **Build and run the Docker container:**
   ```bash
   docker-compose up --build
   ```

3. **Access the portfolio website:**
   Open your browser and navigate to `http://localhost:8080` to view the website.

4. **Stop the container:**
   Once you're done, stop the container with the following command:
   ```bash
   docker-compose down
   ```



## Conclusion

This project demonstrates a simple personal portfolio website served with Nginx in a Docker container. The Docker setup, Git workflow, and GitHub Actions integration provide an efficient development and deployment process.



## Screen Shots

![image](https://github.com/user-attachments/assets/571110fe-e095-485e-beae-ddb128e2e235)

![image](https://github.com/user-attachments/assets/ccb7ae7c-2ce9-47ea-b3e2-ab9c0c280f90)



