# Code

import win32com.client as win32
from pymsg import MSG

def send_email(subject, body, recipients, attachments=None):
    outlook = win32.Dispatch('Outlook.Application')
    mail = outlook.CreateItem(0)
    mail.Subject = subject
    mail.HTMLBody = body
    mail.To = recipients
    
    if attachments:
        for attachment in attachments:
            mail.Attachments.Add(attachment)
    
    mail.Send()
    print("E-mail został wysłany.")

# Przykładowe użycie
subject = "Testowa wiadomość"
template_path = "template.msg"  # Ścieżka do pliku z szablonem .msg
recipients = "example@example.com"  # Adres odbiorcy

# Wczytanie treści szablonu z pliku .msg
msg = MSG(template_path)
template_body = msg.body

# Wywołanie funkcji send_email z treścią z szablonu
send_email(subject, template_body, recipients)
