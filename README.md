

# 🏀 NBA Game Day Notifications System

## **Why I Built This**
As a die-hard NBA fan who's tired of missing crucial game moments, I created this real-time notification system to keep me and fellow basketball enthusiasts in the loop. This project combines my passion for sports with cloud architecture to deliver something I actually use every game day.

---

## **What This System Does**
- 📊 Pulls live NBA scores from a professional sports data API
- 📱 Delivers instant game updates via text/email (no more checking your phone every 5 minutes!)
- ⏱️ Runs on a schedule so you never miss a crucial 4th quarter comeback
- 🔒 Built with security-first mindset (because nobody likes their data exposed)
- ☁️ Deploys in seconds with Terraform (because life's too short for manual setup)

## **Before You Start**
- Free API key from [sportsdata.io](https://sportsdata.io/) (takes 2 minutes to register)
- Your own AWS account (the free tier should cover most usage unless you're texting the entire neighborhood)
- AWS CLI configured to your account
- Terraform v1.10.5+ installed (it's worth learning - trust me!)

---

## **How It All Works**
![NBA Score Pipeline Architecture](https://github.com/user-attachments/assets/5e19635e-0685-4c07-9601-330f7d1231f9)

*Simple but effective: Lambda grabs the data, formats it nicely, and SNS makes sure it reaches your phone/inbox right away*

---

## **Tech Stack I Chose**
- **AWS** for reliable cloud infrastructure
- **Terraform** because clicking through the AWS console 100 times isn't my idea of fun
- **SNS, Lambda, EventBridge** - the perfect trio for event-driven notifications
- **Python** for its simplicity and powerful API handling capabilities
- **IAM Policies** configured with least privilege (because security matters)

---

## **Project Files**
```bash
game-day-notifications_terraform/
├── nba_notifications.py         # Where the magic happens
├── nba_notifications.zip        # Same magic, but zipped for Lambda
├── game_day_notifications.tf    # Infrastructure as code (never manually create resources again!)
├── LICENSE                     
├── .gitignore
└── README.md                    # You're reading it now 👀               # Project documentation
``` 

## **Setup Instructions**

### **Clone the Repository**
```bash
git clone https://github.com/ifeanyiro9/game-day-notifications.git
cd game-day-notifications
```

### **Store API Key as secret in Parameter store**
1. Run this aws cli command with your api key to store it in Paremeter store
```bash
aws ssm put-parameter --name "nba-api-key" --value "<API_KEY>" --type "SecureString"
```

### **Run Terraform commands**
1. Initialize Terraform directory, provider plugins and set up local backend
```bash
terraform init
```
2. Format Terraform config files to make it clean, readable, and follow best practices.
```bash
terraform fmt
```
3. Check Terraform configuration for syntax errors and correctness
```bash
terraform validate
```
4. Show preview of changes Terraform will make to your infrastructure before applying them
```bash
terraform plan
```
5. Create or update the infrastructure based on the Terraform configuration.
```bash
terraform apply
```
6. Remove all resources defined in your Terraform configuration.
```bash
terraform destory
```

### **Add Subscriptions to the SNS Topic**
1. After creating the topic, head on the SNS topic name.
2. Navigate to the Subscriptions tab and click Create subscription.
3. Select a Protocol:
- For Email:
  - Choose Email.
  - Enter a valid email address.
- For SMS (phone number):
  - Choose SMS.
  - Enter a valid phone number in international format (e.g., +1234567890).

4. Click Create Subscription.
5. If you added an Email subscription:
- Check the inbox of the provided email address.
- Confirm the subscription by clicking the confirmation link in the email.

### **Test the System**
1. Open the Lambda function in the AWS Management Console.
2. Create a test event to simulate execution.
3. Run the function and check CloudWatch Logs for errors.
4. Verify that SMS notifications are sent to the subscribed users.

### **What We Learned**
1. Designing a notification system with AWS SNS and Lambda.
2. Securing AWS services with least privilege IAM policies.
3. Automating workflows using EventBridge.
4. Integrating external APIs into cloud-based workflows.
5. Automated the entier solution with Infrastructure as Code tool Terraform
