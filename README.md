#maketrans makes a translation table. suppose shift = 3, a maps to d, b maps to e, etc.
import string
def ceasar_encrypt(message,key):
    shift = key % 26#shifts in increments of 26, cycle of 26 alphabets
    cipher = str.maketrans(string.ascii_lowercase, string.ascii_lowercase[shift: ] + string.ascii_lowercase[:shift])
   # suppose shift = 3, 'abc' is removed;[shift:] = 'defghijlkmnopqrstuvwxyz' and :shift = 'abc'
   #adding them adds the strings to defghijlkmnopqrstuvwxyzabc'
    encrypted_message = message.lower().translate(cipher)
    return encrypted_message

def ceasar_decrypt(encrypted_message, key):
    shift = 26 - (key % 26)
    cipher = str.maketrans(string.ascii_lowercase, string.ascii_lowercase[shift: ] + string.ascii_lowercase[:shift])

    message = encrypted_message.translate(cipher)
    return message

message = input("enter message to encrypt")
key = int(input("enter key value shift"))

encrypted_message = ceasar_encrypt(message,key)
print(f"Encrypted message: {encrypted_message}")

decrypted_message = ceasar_decrypt(encrypted_message, key)
print(f"Decrypted message: {decrypted_message}")

#code to decrypt an encrypted message
#import string


"""def decryption_cmon(ciphertext):
    ciphertext = ciphertext.lower()
    possibilities = []
    for key in range(26):
        shift = 26 - key
        table = str.maketrans(string.ascii_lowercase, string.ascii_lowercase[shift: ] + string.ascii_lowercase[:shift])
        decrypted = ciphertext.translate(table)
        possibilities.append((key,decrypted))
    return possibilities

ciphertext = input("enter text to be decrypted")
all = decryption_cmon(ciphertext)



for key,text in all:
    print(f"Key={key}: {text}")"""
