

# 🏀 NBA Game Day Notifications System

## **Why I Built This**
This isn't just another tech project—it's a love letter to the game, combining my passion for sports with some pretty clever cloud architecture. By leveraging AWS services like SNS, Lambda, and EventBridge, along with NBA APIs, I created an alert system that sends game scores and updates directly to subscribers. And because I'm all about efficiency, I used Terraform to make deploying and tearing down the entire solution as quick as a fast break.

---

## **What This System Does**
- 📊 Pulls live NBA scores from a professional sports data API
- 📱 Delivers instant game updates via text/email 
- ⏱️ Runs on a schedule so you never miss a crucial 4th quarter comeback
- 🔒 Built with security-first mindset 
- ☁️ Deploys in seconds with Terraform

## **Before You Start**
- Free API key from [sportsdata.io](https://sportsdata.io/) 
- Your own AWS account 
- AWS CLI configured to your account
- Terraform v1.10.5+ installed 

---

## **How It All Works**
![NBA Score Pipeline Architecture](https://github.com/user-attachments/assets/5e19635e-0685-4c07-9601-330f7d1231f9)

*EventBridge kicks things off by tracking NBA game schedules, Lambda grabs the data, formats it nicely, and SNS makes sure it reaches your phone/inbox right away*

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
├── game_day_notifications.tf    # Infrastructure as code
├── LICENSE                     
├── .gitignore
└── README.md                    # You're reading it now 👀  
``` 

## **Setup Instructions**


### **First Things First: Grab the Code**
```bash
git clone https://github.com/developedbydmac/game-day-notifications_terraform.git
cd game-day-notifications_terraform
```

### **Secure Your API Key**
Protect that precious NBA API key by storing it safely in AWS Parameter Store:
```bash
aws ssm put-parameter --name "nba-api-key" --value "<API_KEY>" --type "SecureString"
```

### **Terraform Magic: Making Infrastructure Dance**
Let's get your infrastructure rolling with these essential Terraform commands:

1. **Initialize Everything**
```bash
terraform init
```
This sets up all the necessary plugins and gets your project ready to roll.

2. **Keep It Clean**
```bash
terraform fmt
```
A quick formatting pass to make sure your code looks sharp and follows best practices.

3. **Double-Check Your Work**
```bash
terraform validate
```
Catches any sneaky syntax errors before they cause trouble.

4. **Preview the Changes**
```bash
terraform plan
```
See exactly what's about to happen to your infrastructure - no surprises!

5. **Bring It to Life**
```bash
terraform apply
```
Watch your cloud infrastructure come to life with just one command.

6. **Clean Up Time**
```bash
terraform destroy
```
When you're done playing, sweep away everything you've created.

### **Get Those Notifications Rolling**
Time to set up your subscriptions:
1. Head to the SNS topic 
2. Click "Create Subscription"
3. Choose your poison:
   - Email: Enter your email
   - SMS: Drop in your phone number (international format, please!)
4. Confirm your subscription (check that inbox or phone)

### **Kick the Tires**
Make sure everything's working:
1. Jump into the Lambda function in AWS Console
2. Create a test event
3. Run the function
4. Peek at CloudWatch Logs
5. Verify those notifications are flying

### **The Takeaways**
By the end of this, you'll have leveled up in:
- Building slick notification systems with AWS
- Locking down services with rock-solid security
- Automating workflows like a cloud ninja
- Integrating external APIs seamlessly
- Mastering Infrastructure as Code with Terraform