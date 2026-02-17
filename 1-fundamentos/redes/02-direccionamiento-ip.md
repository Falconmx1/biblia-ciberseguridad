# 🧠 Direccionamiento IP y Subredes

> "Una IP es como tu dirección en Internet. Sin ella, eres un vagabundo digital." — Anónimo

## 📍 ¿Qué es una dirección IP?

Una **dirección IP** (Internet Protocol) es un identificador único asignado a cada dispositivo en una red. Como la dirección de tu casa, pero para computadoras.

### Dos versiones principales:
- **IPv4**: 32 bits (ej: 192.168.1.1) → la más común
- **IPv6**: 128 bits (ej: 2001:0db8:85a3:0000:0000:8a2e:0370:7334) → el futuro

## 🔢 Estructura de IPv4

Una dirección IPv4 tiene **4 octetos** (4 números de 0-255 separados por puntos):
192 . 168 . 1 . 1
[red] [red] [red] [host]


### Pero... ¿dónde termina la red y empieza el host? ¡Ahí entran las clases y las máscaras!

## 📊 Clases de IP (Tradicionales)

| Clase | Rango | Máscara por defecto | Uso |
|-------|-------|---------------------|-----|
| **A** | 1.0.0.0 - 126.255.255.255 | 255.0.0.0 (/8) | Grandes empresas |
| **B** | 128.0.0.0 - 191.255.255.255 | 255.255.0.0 (/16) | Medianas empresas |
| **C** | 192.0.0.0 - 223.255.255.255 | 255.255.255.0 (/24) | Pequeñas redes |
| **D** | 224.0.0.0 - 239.255.255.255 | - | Multicast |
| **E** | 240.0.0.0 - 255.255.255.255 | - | Experimental |

## 🏠 IPs Privadas vs Públicas

### IPs Públicas
- Únicas en todo Internet
- Las asigna tu proveedor (ISP)
- Ej: 8.8.8.8 (DNS de Google)

### IPs Privadas (Nunca salen a Internet)
Clase A: 10.0.0.0 - 10.255.255.255
Clase B: 172.16.0.0 - 172.31.255.255
Clase C: 192.168.0.0 - 192.168.255.255

📌 *Estas son las que ves en tu casa/oficina (ej: 192.168.1.1)*

## 🎭 Máscara de Subred (Subnet Mask)

La máscara **separa la parte de red de la parte de host**.

### Formas de escribirla:
Formato decimal: 255.255.255.0
Formato CIDR: /24
En binario: 11111111.11111111.11111111.00000000

### Ejemplos comunes:

| Máscara | CIDR | Nº IPs totales | Nº IPs útiles* |
|---------|------|----------------|----------------|
| 255.0.0.0 | /8 | 16,777,216 | 16,777,214 |
| 255.255.0.0 | /16 | 65,536 | 65,534 |
| 255.255.255.0 | /24 | 256 | 254 |
| 255.255.255.128 | /25 | 128 | 126 |
| 255.255.255.192 | /26 | 64 | 62 |
| 255.255.255.224 | /27 | 32 | 30 |
| 255.255.255.240 | /28 | 16 | 14 |
| 255.255.255.248 | /29 | 8 | 6 |
| 255.255.255.252 | /30 | 4 | 2 |

*\*Las IPs útiles = total - 2 (una para red, una para broadcast)*

## 🧮 Cálculo de Subredes (Fórmula Mágica)

### Para saber cuántas subredes puedes crear:
2^n (donde n = número de bits "prestados" a la máscara)


### Para saber cuántos hosts por subred:

### 🎯 Ejemplo práctico:
Tienes: `192.168.1.0/24` y necesitas 4 subredes

**Paso 1:** ¿Cuántos bits necesitas? 2^n = 4 → n = 2 bits
**Paso 2:** Nueva máscara = /24 + 2 = /26 (255.255.255.192)
**Paso 3:** Las 4 subredes serían:
Subred 1: 192.168.1.0 /26 (hosts: 192.168.1.1 - 192.168.1.62)
Subred 2: 192.168.1.64 /26 (hosts: 192.168.1.65 - 192.168.1.126)
Subred 3: 192.168.1.128 /26 (hosts: 192.168.1.129 - 192.168.1.190)
Subred 4: 192.168.1.192 /26 (hosts: 192.168.1.193 - 192.168.1.254)


## 🛠️ Práctica: Comandos Útiles

### En Windows (CMD):
```cmd
# Ver tu IP y máscara
ipconfig

# Ver tabla de rutas
route print

# Ver conexiones activas
netstat -n

### En Linux/Mac:
bash

# Ver IPs
ip addr show
# o
ifconfig

# Ver tabla de rutas
ip route
# o
route -n

# Escanear tu red local (¡INSTALA NMAP!)
nmap -sn 192.168.1.0/24

🎮 Mini Laboratorio: Calcula Tú Mismo

Ejercicio 1: Tienes la red 10.0.0.0/8. Necesitas 500 subredes.

    ¿Cuántos bits necesitas?

    ¿Cuál sería la nueva máscara?

    ¿Cuántos hosts por subred?

Ejercicio 2: Tienes 172.16.0.0/16 y necesitas subredes con mínimo 1000 hosts cada una.

    ¿Qué máscara usarías?

    ¿Cuántas subredes obtienes?

(Respuestas al final del documento)
📝 Resumen Rápido
Concepto	Fórmula	Ejemplo
IPs totales	2^(32 - CIDR)	/24 → 2^8 = 256
IPs útiles	2^(32 - CIDR) - 2	/24 → 254
Bits de red	CIDR	/24 → 24 bits
Bits de host	32 - CIDR	/24 → 8 bits
🔥 Tips para Hacking/CTFs

    Las IPs que terminan en .0 son la dirección de red (no asignable)

    Las IPs que terminan en .255 son broadcast (no asignable)

    En subredes /30 solo hay 2 IPs útiles (¡típico en enlaces punto a punto!)

    La IP privada más común en routers domésticos: 192.168.1.1 o 192.168.0.1

    La IP de loopback: 127.0.0.1 (¡tu propio equipo!)

📌 Respuestas a los ejercicios:

Ejercicio 1:

    2^n ≥ 500 → n = 9 bits

    Máscara: /8 + 9 = /17 (255.255.128.0)

    Hosts: 2^(32-17) - 2 = 2^15 - 2 = 32766 hosts/subred

Ejercicio 2:

    2^h - 2 ≥ 1000 → 2^10 - 2 = 1022 → h = 10 bits para hosts

    Máscara: /16 + (16-10) = /22 (255.255.252.0)

    Subredes: 2^(22-16) = 2^6 = 64 subredes
