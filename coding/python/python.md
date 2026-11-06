# Python Fundamentals

This will be geared toward networking but still follow the general fundamentals of programming in Python.

## Core Python

### Variables

```python
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

```python
interfaces = [
    "Gi1/0/1",
    "Gi1/0/2",
    "Gi1/0/3"
]
```

## Dictionaries

This will be used constantly

```python
device = {
    "hostname": "NYC-SW01",
    "ip": "10.1.1.1",
    "vendor": "Cisco"
}

print(device["hostname"])
```

### Loops

```python
for interface in interfaces:
    print (interface)
```

### Conditions

```python
status = "down"

if status = "up":
    print("Interface healthy")
else:
    print("Check circuit")
```

### Functions

```python
def show_device(hostname):
    print(hostname)

show_device("NYC-SW01")
```

## Learn File Manipulation

```python
open()
read()
write()
```

```python
with open("show_version.txt") as file:
    output = file.read()

print(output)
```

```python
with open("report.txt","w") as file:
    file.write("Audit Complete")
```

## Error Handling

```python
try:
    ip = device["ip"]
except KeyError:
    print("IP Missing")
```



---
