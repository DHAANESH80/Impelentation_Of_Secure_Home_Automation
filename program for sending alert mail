from email import *
from time import *
from gpio import *

def onEmailReceive(sender, subject, body):
	print("Received from: " + sender)
	print("Subject: " + subject)
	print("Body: " + body)

def onEmailSend(status):
	print("send status: " + str(status))

def main():
	EmailClient.setup(
		"mcu@cisco.com",
		"cisco.com",
		"mcu",
		"password"
	)
	
	EmailClient.onReceive(onEmailReceive)
	EmailClient.onSend(onEmailSend)
	while True:
		temp=digitalRead(0);
		print("temperature",temp);
		if (temp>=200):
			EmailClient.send("pc@cisco.com", "Temperature alert", "temperature is  high")
			print("Temperature is HIGH")
			customWrite(1,HIGH);
		else:
			print("Temperature is Normal");
			customWrite(1,LOW);
		sleep(2);

	# check email once a while
	while True:
		EmailClient.receive()
		sleep(5)

if __name__ == "__main__":
	main()
