# **🤖 Daily Slack Notification – The Daily Assistant for Slack**

The **Daily Slack Notification** is an **automated bot for Slack** that schedules and announces the **daily stand-up meeting**, highlighting who will be responsible for the day's presentation. 🚀

This bot works by creating an **API in Slack** using a **Slack App** with the necessary permissions to send messages to a specific channel.

📌 **How to create a Slack API for this bot?**  
To use this bot, you need to create a **Slack App** and obtain the required tokens. Follow the official Slack documentation:  
🔗 [Create a Slack App](https://api.slack.com/apps)

The process is fully **automated via GitHub Actions**, allowing **scheduled daily execution** via **cron jobs** or manual execution whenever needed.

---

## **📌 Features**

✅ **Automatic daily announcement** in Slack.  
✅ **Sequential selection** of the presenter from the configured members.  
✅ **Correct mention** of the presenter in Slack (using IDs).  
✅ **Automated execution** via **GitHub Actions** with scheduling (`cron`) support.  
✅ **Manual execution** via **GitHub Actions workflow_dispatch**.

---

## **🛠 Technologies Used**

This project was developed using:

- **Python 3.9**
- **GitHub Actions** (for execution automation)
- **Requests** (for integration with the Slack API)

---

## **📂 Project Structure**

The project follows the structure below:

```
.
├── .github/workflows/       # GitHub Actions configuration
│   ├── ci.yaml              # Workflow for automated execution
├── scripts/                 # Directory for Python scripts
│   ├── daily_slack.py       # Script responsible for sending messages to Slack
├── .gitignore               # File to ignore unnecessary files in the repository
├── LICENSE                  # Project license
├── README.md                # Project documentation
```

---

## **🔄 Presenter Selection Logic**

The daily presenter **is selected in sequential order**, ensuring a **fair rotation among members**.

### **📌 How does it work?**

The script maintains a pre-configured list of team members (via `SLACK_MEMBERS`) and selects the **next in line** each day. When all members have presented, the order **resets to the beginning**.

🔹 **Example:**

If `SLACK_MEMBERS="U123456,U654321,U987654"`, the presentation order will be:

1️⃣ Day 1: `U123456`  
2️⃣ Day 2: `U654321`  
3️⃣ Day 3: `U987654`  
4️⃣ Day 4: `U123456` (restarts)

This logic prevents **random selection** and ensures a fair rotation.

---

## **🚀 Setup and Usage**

### **1️⃣ Prerequisites**

Before running the script, ensure you have:

- **Python 3.9+ installed**
- A **Slack bot configured** with permissions to send messages
- The following **environment variables configured** in GitHub Actions:

| Variable        | Description                                              |
| --------------- | -------------------------------------------------------- |
| `SLACK_TOKEN`   | Slack authentication token                               |
| `CHANNEL_ID`    | ID of the channel where the message will be sent         |
| `SLACK_MEMBERS` | List of member IDs for presentation, separated by commas |

💡 **How to get Slack user IDs?**  
If you need user IDs, use the Slack API:  
🔗 [Get Slack User List](https://api.slack.com/methods/users.list/test)

---

### **2️⃣ How to Run the Project Locally?**

1️⃣ **Clone the repository**

```bash
git clone https://github.com/your-username/daily-slack-notification.git
cd daily-slack-notification
```

2️⃣ **Create and activate a virtual environment**

```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows
```

3️⃣ **Install dependencies**

```bash
pip install -r requirements.txt
```

4️⃣ **Set environment variables**

```bash
export SLACK_TOKEN="your_token_here"
export CHANNEL_ID="your_channel_id_here"
export SLACK_MEMBERS="U12345,U67890,U54321"
```

💡 On Windows, use `set SLACK_TOKEN="your_token_here"`

5️⃣ **Run the script**

```bash
python scripts/daily_slack.py
```

---

## **📅 Scheduling via GitHub Actions**

GitHub Actions allows **automatic and manual** execution of the bot.

### **🔹 Automatic Execution**

The bot can be **scheduled** to run at specific times using **cron jobs** in **GitHub Actions**.

📌 **Example configuration (`.github/workflows/ci.yaml`):**

```yaml
name: Daily Slack Notification

on:
  schedule:
    - cron: "30 12 * * 1-5" # Runs at 12:30 PM (UTC) Monday to Friday
  workflow_dispatch: # Allows manual execution via GitHub Actions

jobs:
  daily-slack-notification:
    name: Send Slack Notification
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.9"

      - name: Install dependencies
        run: pip install -r requirements.txt

      - name: Run Python script
        run: python scripts/daily_slack.py
```

🔹 **Note:** The cron job can be adjusted to run at different times and days as needed.

---

## **✅ Testing and Debugging**

If you need to test or debug the code:

1️⃣ Verify that environment variables are set correctly.  
2️⃣ Test the Slack API manually using `requests.post`.  
3️⃣ Use `print()` statements in the code to check variable values before sending the message.

---

## **🚨 Troubleshooting**

### **The bot is not sending messages to Slack**

- Check if the **SLACK_TOKEN** is correct and active.
- Make sure the bot **is present in the correct channel** (`#your-channel`).

### **The bot is not running automatically**

- Confirm that **GitHub Actions is enabled** in the repository.
- Check the workflow history for possible errors.

---

## **📄 License**

This project is under the **MIT License**.

💡 **Developed to help agile teams keep their daily stand-ups organized!** 🚀

---

## **💡 Contributions**

Feel free to open **issues** and **pull requests** for improvements or fixes!

🚀 Made with ❤️ by **Priscila Oliveira**
