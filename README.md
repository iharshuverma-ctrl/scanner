import socket

print("=" * 40)
print("      Python Port Scanner")
print("=" * 40)

target = input("Enter IP Address: ")

ports = [20,21,22,23,25,53,80,110,143,443,3306,8080]

print(f"\nScanning {target}...\n")

for port in ports:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(1)

    result = s.connect_ex((target, port))

    if result == 0:
        print(f" Port {port} is OPEN")
    else:
        print(f" Port {port} is CLOSED")

    s.close()

print("\nScan Completed.")
