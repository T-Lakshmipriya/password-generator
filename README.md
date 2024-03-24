import random
import string

def generate_random_password(length=12, uppercase=True, lowercase=True, digits=True, special_chars=True):
    characters = ""
    
    if uppercase:
        characters += string.ascii_uppercase
    if lowercase:
        characters += string.ascii_lowercase
    if digits:
        characters += string.digits
    if special_chars:
        characters += string.punctuation

    if not any([uppercase, lowercase, digits, special_chars]):
        raise ValueError("At least one character type must be selected.")

    if length < 4 and (uppercase or lowercase or digits or special_chars):
        raise ValueError("Password length should be at least 4 for the selected character types.")

    password = "".join(random.choice(characters) for _ in range(length))
    
    return password

# Specify the length and complexity of the password
password_length = 16
include_uppercase = True
include_lowercase = True
include_digits = True
include_special_chars = True

# Generate a random password
random_password = generate_random_password(
    length=password_length,
    uppercase=include_uppercase,
    lowercase=include_lowercase,
    digits=include_digits,
    special_chars=include_special_chars
)

print("Randomly Generated Password:")
print(random_password)
