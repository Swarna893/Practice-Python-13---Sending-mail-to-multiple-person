# Practice-Python-13---Sending-mail-to-multiple-person

# import smtplib as s
#
# ob = s.SMTP('smtp.gmail.com', 587)
# ob.ehlo()
# ob.starttls()
# ob.login('chandraswarnamoy@gmail.com', 'Sw@rna08')
# subject = "test python"
# body = "I love python"
# message = "subject:{}\n\n{}".format(subject, body)
# listadd = ['saritkumarchandra@gmail.com', 'sulagnarumki@gmail.com']
# ob.sendmail('chandraswarnamoy@gmail.com', listadd, message)
# print("MAIL SENT....!!!!")
# ob.quit()

import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart


def send_email(subject, message, to_emails, smtp_server, smtp_port, smtp_username, smtp_password):
    # Create the MIME object
    msg = MIMEMultipart()
    msg['From'] = smtp_username
    msg['To'] = ', '.join(to_emails)
    msg['Subject'] = subject

    # Attach the message to the email
    msg.attach(MIMEText(message, 'plain'))

    # Connect to the SMTP server
    with smtplib.SMTP(smtp_server, smtp_port) as server:
        # Log in to the SMTP server
        server.login(smtp_username, smtp_password)

        # Send the email
        server.sendmail(smtp_username, to_emails, msg.as_string())


# Replace these variables with your own values
subject = "HAPPY NEW YEAR - 2K24"
message = "Wish you a very happy new year. May this year brings you a lot of happiness and surprises. Fun Fact - This message is sent using programming"
to_emails = ["saritkumarchandra@gmail.com", "sulagnarumki@gmail.com",]
smtp_server = "your_smtp_server.com"
smtp_port = 587  # Use the appropriate port for your SMTP server
smtp_username = "chandraswarnamoy@gmail.com"
smtp_password = "Jerry2@18"

# Send the email
send_email(subject, message, to_emails, smtp_server, smtp_port, smtp_username, smtp_password)

