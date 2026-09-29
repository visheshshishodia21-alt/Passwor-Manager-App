# Passwor-Manager-App

import random
import string

passwords = {}

#load existing password file
try:
    with open("passwords.text","r") as file:
        for line in file:
            website,pwd = line.strip().split(":")
            passwords[website] = pwd

except:
    pass

def generate_password():
    chars =string.ascii_letters + string.digits + "!@#$%^&"
    password = "".join(random.choice(chars) for _ in range(8))
    return password

while True:
    print("\n-----PERSONAL PASSWORD MANAGER-----")
    print("1.Save passwords")
    print("2.View passwords")
    print("3.Generate passwords")
    print("4.Exist")

        
    choice = input("Enter Your Choice:")

    if choice == "1":
        site = input("enter website:")
        pwd = input("enter password:")

        passwords[site] = pwd

        with open("password.txt","a") as file:
            file.write(f"{site}:{pwd}\n")

        print("saved!")

    elif choice == "2":
        if not passwords:
            print("No data")

        else:
            for site,pwd in passwords.items():
                print(site,":",pwd)

    elif choice == "3":
        print("Generated Password", generate_password())

    elif choice == "4":
        print("ok lulu..")
        break

    else:
        print("in valid input")