Deploying a web application to Azure from GitHub involves several steps, including creating a repository on GitHub, setting up an Azure Web App, and configuring continuous deployment. Below is a step-by-step guide with example code.

### Step 1: Create a GitHub Repository

1. Go to [GitHub](https://github.com/) and create a new repository.
2. Clone the repository to your local machine.

```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

### Step 2: Create a Simple Web Application

For this example, we'll create a simple Node.js application. You can replace this with your own application.

```bash
mkdir myapp
cd myapp
npm init -y
npm install express
```

Create a file `app.js` with the following content:

```javascript
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => {
  res.send('Hello, Azure!');
});

app.listen(port, () => {
  console.log(`App running on http://localhost:${port}`);
});
```

### Step 3: Commit and Push to GitHub

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

### Step 4: Create an Azure Web App

1. Go to the [Azure Portal](https://portal.azure.com/).
2. Click on "Create a resource" and select "Web App".
3. Fill in the required details such as App name, Resource group, and Runtime stack (e.g., Node.js).

### Step 5: Configure Deployment from GitHub

1. In the Azure Portal, navigate to your newly created Web App.
2. Go to "Deployment Center".
3. Select "GitHub" as the source.
4. Authenticate with GitHub if prompted.
5. Select your repository and branch (e.g., `main`).
6. Click "Save".

Azure will now set up continuous deployment. Every time you push changes to your GitHub repository, Azure will automatically deploy them to your Web App.

### Step 6: Test the Deployment

1. Once the deployment is complete, navigate to the URL of your Azure Web App (e.g., `https://your-app-name.azurewebsites.net`).
2. You should see "Hello, Azure!" displayed on the page.

### Step 7: Make Changes and Redeploy

1. Make changes to your application locally, for example, updating `app.js`:

```javascript
app.get('/', (req, res) => {
  res.send('Hello, Azure! Updated.');
});
```

2. Commit and push the changes to GitHub:

```bash
git add app.js
git commit -m "Update greeting message"
git push origin main
```

Azure will automatically detect the changes and redeploy your application.

Following these steps, you can continuously deploy any web application to Azure from GitHub.
