# EC2 Instance Setup and Registration Form Application Deployment

This guide walks you through the process of setting up an EC2 instance, installing MongoDB, and deploying a registration form application.

## Step 1: Create an EC2 Instance

1. **Launch an EC2 instance**:
   - Choose the Ubuntu version (Ubuntu Server 22.04 LTS).
   - Configure the instance as needed.
   - Launch the instance.

## Step 2: Connect to the Instance

1. **Connect to the instance**:
   - Use an SSH client to connect to your EC2 instance.
   - Example command: `ssh -i "your-key-pair.pem" ubuntu@your-ec2-public-dns`

## Step 3: Set Up the Environment

1. Switch to the root user:
   ```sh
   sudo su
   ```

2. Install required packages:
   ```sh
   sudo apt-get install gnupg curl
   ```

3. Add MongoDB GPG key:
   ```sh
   curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg --dearmor
   ```

4. Add MongoDB repository:
   ```sh
   echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
   ```

5. Update package list:
   ```sh
   sudo apt-get update
   ```

6. Install MongoDB:
   ```sh
   sudo apt-get install -y mongodb-org
   ```

7. Clone the registration application repository:
   ```sh
   git clone https://github.com/vandanamv/Registration-form-.git
   ```

8. Change directory to the cloned repository:
   ```sh
   cd registration
   ```

9. Set up Node.js environment:
   ```sh
   curl -fsSL https://deb.nodesource.com/setup_21.x | sudo -E bash -
   ```

10. Install Node.js:
    ```sh
    apt-get install nodejs -y
    ```

11. Verify Node.js installation:
    ```sh
    node -v
    ```

12. Verify npm installation:
    ```sh
    npm -v
    ```

13. Edit `server.js` file using `vi`:
    ```sh
    vi server.js
    ```
    or using `nano`:
    ```sh
    nano server.js
    ```

14. Install Express.js:
    ```sh
    npm install express
    ```

15. Start the server:
    ```sh
    node server.js
    ```

## Step 4: Access the Application

1. Copy the public IP address of your EC2 instance.
2. Paste it into a new tab in your web browser.

   You should see the registration form.

## Step 5: Register a User

1. Fill out the registration form.
2. Submit the form.

   You should see a message indicating that registration is successfully completed.

## Step 6: Verify Data

1. Check the EC2 terminal for saved registration data.
   
   The terminal should display the details of the registered user, confirming successful data storage.

Congratulations! You have successfully deployed the registration form application on your EC2 instance.
