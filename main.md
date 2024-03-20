🔨🌟Build Your First GitHub Workflow in Minutes ⏱️✨

Ever wished there was a way to automate repetitive tasks in your development workflow?🤔 Look no further than GitHub Actions!

This powerful feature lets you define workflows that run specific actions in response to events like pushes, pull requests, or scheduled times.

This guide will walk you through creating your first GitHub workflow, teaching you the essential steps and components.

To get started It is better to understand the basic terminologies you will use:

1. **Workflow:** This is a set of steps that automatically run based on a given trigger.
2. **Workflow file:** This is file that contains all of the instructions that dictate what happens when the workflow runs.
3. **Trigger:** This refers to the event that causes your workflow to run. Think of it as flipping the switch that starts your automation process.
4. **Job:** This is a single unit within a workflow that performs a given task.
5. **Runner:** This is the virtual machine that runs your workflow jobs.
6. **Step:** This is where the rubber meets the road. A step performs the necessary tasks. They run the scripts, checkout code, or actions and are executed on runners.

By understanding these core terms, you’ll have a solid foundation for building and customizing your GitHub workflows to automate repetitive tasks and streamline your development process.

### Let's create our first workflow

**Setting up the stage:**

1. **Create a repository:** If you don’t have one already, head over to GitHub and create a new repository. This will be the home for your project and workflows.
![creating repo](https://github.com/169398/Github-Workflow/assets/137810838/7f5e14ad-3614-4c39-b5ba-f6b6ac10704a)


2. **Prepare the `.github` Directory:** Navigate to your repository’s root directory on GitHub. Here, create a new directory named `.github`. This directory will house all your workflow configuration files.

3. **Create Your Workflow File:** Inside the `.github/workflows` directory, create a new file with a `.yml` extension.

![workflowfile](https://github.com/169398/Github-Workflow/assets/137810838/3231e60b-3b3c-4dba-82ac-573b7c925029)

```yaml
name: Your_Workflow_Name
on:
  push:
    branches: [ main ]
jobs:
  your-job-name:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        run: echo "This is step 1"
      - name: Step 2
        run: echo "This is step 2" 
```
**Adding the workflow components:**

Now comes the magic✨ Let’s explore the common components that make up a workflow

Triggers: This defines when your workflow should run. For instance:
```yaml

on:
  push:
    branches: [ main ]
This workflow will run whenever there’s a push to the main branch.

Jobs: Each job represents a specific task you want to execute. Define jobs using the jobs keyword followed by a unique identifier and a descriptive name.
yaml
Copy code
jobs:
  build:
    runs-on: ubuntu-latest
    timeout-minutes: 15
```
We specify where it runs on and the timeout time for it to run. You can add any time.

Steps: Steps are individual commands that run within a job. They can involve checking out code, installing dependencies, running tests, or deploying your application. Use the steps keyword within a job to define these steps.
```yaml
Copy code
jobs:
  build:
    name: Build and Test
    steps:
      - uses: actions/checkout@v3  
      - name: Run Build Script
        run: ./build.sh  
      - name: Run Tests
        run: ./test.sh
```
Your final workflow should be similar to this for practice 👇

```yaml
Copy code

name: Lint and Test
on:
  push:
    branches: [ main ]
jobs:
  lint-test:
    name: Run Linters and Tests
    runs-on: ubuntu-latest  
    steps:
      - uses: actions/checkout@v3  
      - name: Use Node.js 16
        uses: actions/setup-node@v3
        with:
          node-version: 16  
      - name: Install Dependencies
        run: npm install  
      - name: Run Linters
        run: npm run lint  
      - name: Run Tests
        run: npm run test
```
Testing Your Workflow:

To test your workflow, push a change to your repository and click on the actions button. You will see the commit message that invoked the workflow. It may be queued then complete then you can click the commit message followed by the text and you will see the output for each step inside that job.
![final workflow](https://github.com/169398/Github-Workflow/assets/137810838/862c7c81-9166-42f9-af10-d7ed043dc25c)


🎉🚀 Woohooo! Congratulations! 🎉🚀 You have successfully created and run your first Github Actions Workflow 🎉✨

This is just a basic example, and GitHub Actions offers a wide range of features to customize your workflows.🛠️💻 Explore the official documentation https://docs.github.com/en/actions to understand more about Github actions.


Thank you for reading .I hope you found this helpful
