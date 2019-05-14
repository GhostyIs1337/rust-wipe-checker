import bs4, requests, smtplib

getPage = requests.get('https://just-wiped.net/rust_servers/376301')
getPage.raise_for_status()

menu = bs4.BeautifulSoup(getPage.text, 'html.parser')

wipes = menu.select('.wipe-date')

print(wipes)

date_of_wipe = '02.05.2019'
flength = len(date_of_wipe)
isTrue = False
toAddress = ['receiver@email.com', 'receiver2@email.com']

for wipe in wipes:
    for i in range(len(wipe.text)):
        chunk = wipe.text[i:i+flength].lower()
        if chunk == date_of_wipe:
            isTrue = True
            print(isTrue)
            if isTrue == True:
                print('Entered IF statement')
                conn = smtplib.SMTP('smtp.gmail.com', 587)
                print(conn)
                conn.ehlo()
                conn.starttls()
                conn.login('sender@email.com', 'private key')
                conn.sendmail('sender@email.com', toAddress, 'Subject: [EU] Facepunch Hapis notification\n\nAttention!\n\nServer just got wiped!\nCommence base building!')
                conn.quit()
                print('Sent notificaton e-mails for the following recipients:\n')
                for i in range(len(toAddress)):
                    print(toAddress[i])
                print('')
