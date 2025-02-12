import socket
import sys
import threading

def scan_port(host, port):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((host, port))
        if result == 0:
            print(f"Porta {port} aberta")
        sock.close()
    except socket.error as err:
        print(f"Erro ao tentar conectar à porta {port}: {err}")


def scan_ports(host, start_port, end_port):
    threads = []
    for port in range(start_port, end_port + 1):
        thread = threading.Thread(target=scan_port, args=(host, port))
        threads.append(thread)
        thread.start()

    for thread in threads:
        thread.join()

if len(sys.argv) != 4:
    print("Uso: python scanner.py <host> <porta_inicial> <porta_final>")
    sys.exit(1)

host = sys.argv[1]
start_port = int(sys.argv[2])
end_port = int(sys.argv[3])

scan_ports(host, start_port, end_port)
