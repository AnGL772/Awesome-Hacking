# Ethisches Hacking — Kleines Lern‑Labor (Docker)

Wichtig: Führe Tests nur in dieser lokalen/isolierten Laborumgebung oder auf Systemen durch, für die du eine ausdrückliche Genehmigung hast.

Kurz: Dieses Labor startet eine verwundbare Web‑App (OWASP Juice Shop) als Ziel und eine Kali‑Container‑Umgebung als Angreifer‑Shell. Damit kannst du lernen, wie man Netzwerke/Services entdeckt und wie typische Werkzeuge aussehen — alles lokal.

Voraussetzungen
- Docker und Docker Compose installiert
- Grundkenntnisse in der Kommandozeile

Schnellstart
1. Repository klonen / in das Verzeichnis wechseln.
2. docker compose up -d
3. Juice Shop: http://localhost:3000
4. Kali: docker exec -it kali /bin/bash (oder /bin/sh)

Erste, sichere Übungen
- Dienste erkennen: nmap --reason -sV -p- localhost  
  (nur zur Übung auf deiner eigenen Maschine / Lab)
- HTTP prüfen: curl -I http://localhost:3000
- Web‑Vulnerability‑Scanner (nur info): nikto -h http://localhost:3000
- Proxy / Analyse: Starte OWASP ZAP oder Burp als Proxy und beobachte HTTP‑Requests aus dem Browser — analysiere Parameter und Header.

Hinweis zu Container-Netzwerk:
- Vom Host erreichst du die Juice Shop Instanz über http://localhost:3000.
- Vom Kali‑Container auf den Juice Shop: curl http://juice-shop:3000 (Service‑Name funktioniert, da beide im selben Docker‑Netzwerk sind).

Was du nicht tun solltest
- Nicht dieselben Techniken an fremden Webseiten/Servern ohne Erlaubnis anwenden.
- Keine automatisierten Angriffe auf Dritt‑Hosts.

Lernpfad (Vorschlag)
1. Netzwerkgrundlagen, TCP/IP, HTTP  
2. Scanning & Enumeration (nmap, netstat)  
3. Web‑Basics & OWASP Top Ten  
4. Web‑Interception & Analyse (Burp/ZAP)  
5. Exploit‑Workflows nur im Lab — danach Absicherung und Patchen lernen

Ressourcen
- OWASP Juice Shop: https://owasp.org/www-project-juice-shop/  
- OWASP Top Ten  
- TryHackMe, Hack The Box (legale CTFs)  
- Bücher: „The Web Application Hacker's Handbook"

Beispielbefehle (im Kali‑Container)
- apt update && apt install -y nmap nikto curl
- nmap -sV -p 3000 juice-shop
- curl http://juice-shop:3000

Wenn du möchtest, kann ich:
- das docker‑compose.yml für dieses Lab in dein Repo anlegen (PR),
- zusätzliche Ziele (DVWA, WebGoat) hinzufügen,
- eine Schritt‑für‑Schritt‑Übung (Beginner → Fortgeschritten) schreiben.