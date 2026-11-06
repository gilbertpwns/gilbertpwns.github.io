# Python Fundamentals

This will be geared toward networking but still follow the general fundamentals of programming in Python.

## Core Python

### Variables

```
hostname = "NYC-SW01"
ip_address = "10.0.0.1"
uptime = 356
```

### Data Types 

string = "Cisco"

integer = 24

float = 3.14

boolean = True

## Lists

```
interfaces = [
    "Gi1/0/1",
    "Gi1/0/2",
    "Gi1/0/3"
]
```

## Dictionaries

This will be used constantly

```
device = {
    "hostname": "NYC-SW01",
    "ip": "10.1.1.1",
    "vendor": "Cisco"
}

print(device["hostname"])
```

### Loops

```
for interface in interfaces:
    print (interface)
```

### Conditions

```
status = "down"

if status = "up":
    print("Interface healthy")
else:
    print("Check circuit")
```

---
