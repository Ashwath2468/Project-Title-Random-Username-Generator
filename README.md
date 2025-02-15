# Project-Title-Random-Username-Generator
import random

a = ["Cool", "Happy", "Brave", "Silly", "Clever", "Mighty", "Swift", "Fierce", "Charming", "Witty"]
n = ["Tiger", "Dragon", "Phoenix", "Wolf", "Eagle", "Shark", "Panda", "Lion", "Bear", "Fox"]

def g(num, sp, lng):
    u = f"{random.choice(a)}{random.choice(n)}"
    if num: u += str(random.randint(1, 99))
    if sp: u += random.choice("!@#$%^&*_-+={}[]|;':\",./<>?")
    return u[:lng] if lng else u

def s(u, f="Username.txt"):  # Filename changed to Username.txt
    try: open(f, 'w').write('\n'.join(u)); print(f"Saved to {f}")
    except Exception as e: print(f"Error: {e}")

def yn(p):
    while True: i = input(p).strip().lower(); return i == 'yes' if i in ('yes', 'no') else print("Invalid")

def i(p, m=None):
    while True:
        try: v = int(input(p)); return v if m is None or v >= m else print(f"At least {m}")
        except: print("Invalid int")

def main():
    print("Usernames")
    num = yn("Numbers? ")
    sp = yn("Special chars? ")
    lng = i("Max length (0 for no limit): ", 0) or None
    c = i("How many? ", 1)
    u = [g(num, sp, lng) for _ in range(c)]
    for x in u: print(f"Generated: {x}")
    if yn("Save? "): s(u)

if __name__ == "__main__": main()
