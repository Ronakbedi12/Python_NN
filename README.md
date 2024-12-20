# Email Sender

from email.message import EmailMessage
import ssl
import smtplib
from passs import pas

email_sender='bedironak822@gmail.com'
email_password=pas

email_receiver="uraniumblast45@gmail.com"

subject="Details"

body="""
name="Ronak Bedi"
college="BK BIET"
branch="AI"
"""
em=EmailMessage()
em['From']=email_sender
em['To']=email_receiver
em['subject']=subject
em.set_content(body)

context=ssl.create_default_context()

with smtplib.SMTP_SSL('smtp.gmail.com',465,context=context) as smtp:
    smtp.login(email_sender,email_password)
    smtp.sendmail(email_sender,email_receiver,em.as_string())
