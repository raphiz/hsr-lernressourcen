# Vorbesprechung InfSi1 19.07.16
## TLS / Zertifikate
Problematik Root CA: Root-Zertifikate sind Self-signed (signiert von sich selbst).

Es dürfen nicht irgendwelche Root-CA importiert werden. Der "zweite" Kanal basiert auf Vertrauen, z.B. dass Microsoft gültige Zertifikate in Windows mitliefert

Wie Entscheided der Browser, wo Zertifikate abgelegt werden? (Zertifizierungsstellen, Personen, Server)
- Wenn self-signed, ist es CA
- Extension Basic-Constraints: CA auf "true"

**Null-Encryption**  
- Schlüsselaustausch wird gemacht, aber die Datenpakete werden im Klartext übertragen
- Gut zum testen, aber Gefahr, wenn ein Attacker ein Downgrade auf Null-Encryption machen kann

**Public-Key Pinning**  
Browser speichert Public-Key einer Domain. Bei einem gefälschten Zertifikat (z.B. Phishing-Seite) wird es nicht angenommen
Problem, wenn Website Zertifikat ändern.  
Problem, wenn Website Zertifikat austauscht. Lösung: Zusätzlich Public-Key einer Intermediate CA angeben, womit das neue Zertifikat signiert wird.

## Harddisk-Encryption
Veracrypt-Passwort sollte 20 Zeichen lang sein, um 128bit zu erreichen. Dieses Passwort wird dann benutzt, um das eigentliche Passwort der Festplatten-Verschlüsselung symmetrisch zu verschlüsseln

## Recht
- Man sollte mit dem Hacking- und Virentatbestand vertraut sein und wissen, welches Delikt unter welchen Tatbestand fällt
- Arp-Spoofing fällt schon unter den Virentatbestand (ändern des ARP-Caches)

## Selbststudium BSI:
- Man sollte die Fragen beantworten können, wenn "man den Bericht gelesen hat"
- Kann grundsätzlich sein, wie z.B. "Wie viele Seiten (ca) hat das Dokument"
- Einleitung und Management Summary sicher verstehen
- Am wichtigsten: "Was steht da drin"

## Kerberos
- Nicht im Detail kennen
- Was ist speziell? "Challenge" ist die Zeit -> Zeitsynchronisation
- Schwachstelle: Der Master-Key ist "nur" ein Hash des Windows-Passworts
    - Übertragung des Chiffres E(time, Masterkey) ist nicht verschlüsselt. Damit kann eine Offline Brute-Force-Attacke durchgeführt werden
    - Sicherer: z.B. Smartcard

## PGP
- Aufgabe zu PGP wird kommen (Danke Patrick!)
- Unterschied zu CA: Schlüssel werden von anderen Teilnehmern unterschrieben



## Praxis-Teil
- Es kommt wahrscheinlich Aufgabe zu Proxy, Stichwort TLS-Traffic sniffen (zumindest konzeptionell)
- Mit eigenem Zertifikat muss signiert und verschlüsselt werden können
