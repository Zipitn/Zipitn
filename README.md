- 👋 Hi, I’m @Zipitn
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Zipitn/Zipitn is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->import marshal

data = {'name': 'John', 'age': 30, 'city': 'Example City'}

# Dumping the data to a file
with open('data_file.marshal', 'wb') as file:
    marshal.dump(data, file)

# Loading the data back
with open('data_file.marshal', 'rb') as file:
    loaded_data = marshal.load(file)

print(loaded_data)
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
import schedule
import time

def send_email():
    # Your email and password
    sender_email = 'your_email@example.com'
    sender_password = 'your_email_password'

    # Recipient email address
    recipient_email = 'recipient@example.com'

    # Message content
    subject = 'Daily Report'
    body = 'This is your daily report content.'

    # Setting up the MIME
    message = MIMEMultipart()
    message['From'] = sender_email
    message['To'] = recipient_email
    message['Subject'] = subject
    message.attach(MIMEText(body, 'plain'))

    # Connect to the SMTP server
    with smtplib.SMTP('smtp.example.com', 587) as server:
        server.starttls()
        # Login to your email account
        server.login(sender_email, sender_password)
        # Send email
        server.sendmail(sender_email, recipient_email, message.as_string())

# Schedule the job to run daily at a specific time
schedule.every().day.at("08:00").do(send_email)

# Run the scheduled jobs
while True:
    schedule.run_pending()
    time.sleep(1)
