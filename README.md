# Password Manager
Creating a place to store passwords iteratively 


Python Password Manager




AES Encryption
The encryption method used in this program comes from the python library PyCryptoDome. This program uses AES encryption methods to store sensitive data (in this case passwords) into a json file.

Hash Verification
To authenticate the user, they are prompted to create a master password (that is also used to decrypt data) which is then stored using a SHA256 Hash Function and is verified at login. Whenever the user is prompted to verify their master password, the password they enter is compared to the hash of the stored master password and access if granted if the two hashes match.

if os.path.isfile("db/masterpassword.json"): # loading json file with stored password.
      with open("db/masterpassword.json", 'r') as jsondata:
          jfile = json.load(jsondata)

      stored_master_pass = jfile["Master"] # retrieving stored hash and saving to a variable.
      master_password = getpass.getpass("Enter your Master password: ") # asking user to enter their master password
      
      # comparing the two hashes
      if SHA256(master_password.encode('utf-8')).hexdigest() == stored_master_pass:
        #rest of program executes
