# 🌐 Introducción a Redes de Computadoras

## ¿Qué es una red?
Una red de computadoras es un conjunto de dispositivos interconectados que comparten recursos e información.

## Tipos de redes según su alcance

| Tipo | Siglas | Descripción |
|------|--------|-------------|
| PAN | Personal Area Network | Red muy pequeña (unos metros), como Bluetooth |
| LAN | Local Area Network | Red de área local (oficina, casa) |
| MAN | Metropolitan Area Network | Red que cubre una ciudad |
| WAN | Wide Area Network | Red de gran cobertura (Internet) |

## Modelo OSI (7 capas)

| Capa | Nombre | Función principal | Ejemplo |
|------|--------|-------------------|---------|
| 7 | Aplicación | Interfaz con el usuario | HTTP, FTP, SMTP |
| 6 | Presentación | Formato de datos, cifrado | SSL, JPEG, ASCII |
| 5 | Sesión | Control de diálogo | NetBIOS, RPC |
| 4 | Transporte | Conexión extremo a extremo | TCP, UDP |
| 3 | Red | Direccionamiento y ruteo | IP, ICMP |
| 2 | Enlace | Acceso al medio físico | Ethernet, Wi-Fi |
| 1 | Física | Transmisión de bits | Cables, ondas |

## Modelo TCP/IP (4 capas)

1. **Aplicación** (HTTP, FTP, DNS)
2. **Transporte** (TCP, UDP)
3. **Internet** (IP)
4. **Acceso a red** (Ethernet, Wi-Fi)

## 📝 Ejercicio práctico
Abre tu terminal (o cmd en Windows) y escribe:
```bash
# Ver tu dirección IP
ipconfig  # En Windows
ifconfig  # En Linux/Mac

# Hacer ping a un servidor
ping google.com

🔍 Conceptos clave para recordar

    Una red conecta dispositivos

    OSI tiene 7 capas teóricas

    TCP/IP tiene 4 capas prácticas

    Cada capa tiene una función específica

📚 Recursos adicionales

    Video: ¿Cómo funciona Internet? (CoreDumped)

    Curso gratuito: Redes desde cero
