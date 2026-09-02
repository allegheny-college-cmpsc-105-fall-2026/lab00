# Lab00: Software Setup Guide

Follow these steps to set up your laptop with the necessary tools for CMPSC105 and other CS/DS courses. This includes installing an Integrated Development Environment (IDE, the place where we'll write code), package manager, and Python. Additionally, we will configure GitHub for accessing and submitting assignments.

## 1. Install Visual Studio Code (IDE)
1. Go to [code.visualstudio.com](https://code.visualstudio.com/) and download the installer for your operating system.
2. Run the installer and follow the default prompts. 
3. Once installed, open VS Code, click the **Extensions** icon on the left sidebar (the four squares), and search for **Python**. Install the official Python extension published by Microsoft.

## 2. Install uv (Package Manager)
`uv` is a lightning-fast Python package and project manager. Open your computer's terminal:
*   **Mac users:** Open the **Terminal** app.
*   **Windows users:** Open **PowerShell**.

Copy and paste the appropriate command for your system and press **Enter**:

**Mac:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows:**
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
*Note: Once the installation finishes, close your terminal and open a fresh one so the changes take effect.*

## 3. Install the Latest Stable Python
In your newly opened terminal, run this single command to let `uv` download and install the latest stable version of Python:
```bash
uv python install
```
To verify it worked, run `uv python list` to see your newly installed Python version.

## 4. Create a GitHub Account
1. Go to [github.com](https://github.com/) and click **Sign up**.
2. Follow the prompts to create your account. We highly recommend using your `@allegheny.edu` email address so you can easily verify your student status later for free GitHub Pro features.
3. Complete the email verification step.

## 5. Generate SSH Keys
SSH keys allow you to securely submit code without typing your password every time. Open your terminal again and run the following command, replacing the email with the one you used to sign up for GitHub:

```bash
ssh-keygen -t ed25519 -C "your_username@allegheny.edu"
```
*   When prompted to "Enter a file in which to save the key," just press **Enter** to accept the default location.
*   When asked for a passphrase, you can press **Enter** twice to leave it empty (this is recommended for beginners so you don't have to type a password every time you submit homework).

## 6. Link Your SSH Key to GitHub
First, you need to display your new public key so you can copy it. Run the command for your operating system:

**Mac:**
```bash
cat ~/.ssh/id_ed25519.pub
```

**Windows:**
```powershell
type ~/.ssh/id_ed25519.pub
```

1. Highlight and copy the entire output (it should start with `ssh-ed25519` and end with your email).
2. Go to GitHub, click your profile picture in the top right, and select **Settings**.
3. On the left sidebar, click **SSH and GPG keys**.
4. Click the green **New SSH key** button.
5. Give it a title (like "My Laptop"), leave the type as "Authentication Key", and paste your copied key into the "Key" box.
6. Click **Add SSH key**.

---

### Verification Step
To verify that your SSH connection works, run the following command in your terminal:
```bash
ssh -T git@github.com
```
You should see a success message welcoming you by your GitHub username.

## 7. Clone the Lab Repository
Now that your SSH key is set up, you can securely download (clone) the lab files to your laptop.
1. In your terminal, navigate to the folder where you want to keep your coursework (e.g., `cd Documents`).
2. Run the following command to clone the starter repository:
   ```bash
   git clone git@github.com:allegheny-college-cmpsc-105-fall-2026/lab00.git
   ```

## 8. Test Python in VS Code
1. Open **Visual Studio Code**.
2. Go to **File > Open Folder...** (or **Open...** on Mac) and select the `lab00` folder you just cloned.
3. In the file explorer on the left sidebar, click on `hello.py` to open the script.
4. Open an integrated terminal in VS Code by going to **Terminal > New Terminal** in the top menu.
5. Run the script using `uv`:
   ```bash
   uv run hello.py
   ```
   *Note: `uv run` will automatically ensure it is using the correct Python version. You should see the output of the script printed to your terminal.*

## 9. Install Jupyter and Notebook Requirements
To run interactive data exploration notebooks, you will need the Jupyter extension and the Python kernel.
1. Click the **Extensions** icon on the left sidebar in VS Code.
2. Search for **Jupyter** (published by Microsoft) and click **Install**.
3. In your VS Code terminal, create a virtual environment for this repository and install the `ipykernel` package:
   ```bash
   uv add ipykernel
   ```
   *Note: uv add will automatically create the virtual environment (.venv) and update your project dependencies.*

## 10. Open and Run the Notebook
1. In the VS Code file explorer, click on `demo.ipynb` to open the notebook.
2. In the top right corner of the notebook interface, click **Select Kernel** (it might currently say "Python").
3. Choose **Python Environments** and select the environment marked with `('.venv': venv)` that you just created.
4. Click the "Play" button next to the first code cell to run it. If VS Code prompts you to install any additional dependencies for the kernel, go ahead and click "Install".
