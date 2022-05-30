# Como-mandar-E-mail-python
Mandar email porm meio da biblioteca smtp e email mensage no python.

import os
import smtplib
from email.message import EmailMessage

seu_email = 'Seu E-mail'
sua_senha_do_email = 'Senha do seu E-mail'

msg = EmailMessage()
msg['Subject'] = 'Assunto do email'
msg['From'] = 'Seu email'
msg['To'] = 'Para quem(email da pessoa que voce ira enviar o email)'
msg.set_content('Email')

with smtplib.SMTP_SSL('smtp.gmail.com',465) as smtp:
    smtp.login(seu_email, sua_senha_do_email)
    smtp.send_message(msg)



#MODO 2 MANDAR E-MAIL COM PARAGRAFOS.

import os
import smtplib
import email.message


#O <p> tem a funçao de abrir um paragrafo para seu email ja o </p> tem a funçao de fechar o paragrafo.
corpo_do_email = """
    <p>Parágrafo1</p>
    <p>Parágrafo2</p>
    <p>Susetivamente</>
    """

msg = email.message.Message()
msg['Subject'] = 'Assunto do email'
msg['From'] = 'Seu email'
msg['To'] = 'Para quem(email da pessoa que voce ira enviar o email)'

senha_email = 'sua senha'
msg.set_payload(corpo_do_email)

g = smtplib.SMTP('smtp.gmail.com: 587')
g.starttls()
g.login(msg['From'], [msg['To']], msg.as_string().encode('utf-8'))
print('Email enviado')
