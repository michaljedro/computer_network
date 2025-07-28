# 🌐 Projekt Sieci Komputerowej dla Organizacji Wielooddziałowej

Ten projekt przedstawia kompletną implementację sieci komputerowej dla organizacji składającej się z 12 oddziałów, z których każdy zatrudnia 13 pracowników. Zastosowano separację sieci VLAN, adresację IPv4 oraz dostęp warunkowy dla Biura Informatyki do zasobów wszystkich lokalizacji.

---

## 📌 Założenia Projektowe

- 🏢 **12 oddziałów**, każdy z 13 użytkownikami
- 🔐 Oddziały odseparowane sieciowo (VLAN + routing)
- 🛠️ **Biuro Informatyki** z pełnym dostępem administracyjnym do każdej sieci
- 🌐 Statyczna lub dynamiczna adresacja IP (DHCP)
- 🔒 Prosta segmentacja i filtrowanie ruchu (ACL)
- 🧰 Projekt wykonany w **Cisco Packet Tracer 8.2.2**

---

## 🗺️ Topologia Sieci

![Network Topology](docs/topology-diagram.png)

> Plik z topologią znajduje się w katalogu `pkt/final-project.pkt`.

---

## 🧮 Plan Adresacji

Zobacz: [`docs/addressing-plan.md`](docs/addressing-plan.md)

| Oddział | VLAN | Adresacja           | Gateway        |
|---------|------|---------------------|----------------|
| 01      | 10   | 192.168.10.0/24     | 192.168.10.1   |
| 02      | 20   | 192.168.20.0/24     | 192.168.20.1   |
| ...     | ...  | ...                 | ...            |
| IT      | 100  | 10.10.100.0/24      | 10.10.100.1    |

---

## 🧩 Kluczowe Komponenty

### VLAN-y i Segmentacja
- Każdy oddział pracuje we własnej VLAN (izolacja warstwy 2).
- Biuro IT ma dostęp do wszystkich VLAN przez inter-VLAN routing.

### Routing i dostęp
- Użyto router-on-a-stick lub L3 switch do routingu między VLAN.
- ACL ograniczające dostęp między oddziałami, z wyjątkiem IT.

### DHCP i DNS
- Centralny serwer DHCP dla każdego VLAN.
- Przykładowe konfiguracje znajdują się w folderze `configs/`.

---

## 📂 Zawartość Repozytorium

| Folder         | Opis |
|----------------|------|
| `docs/`        | Dokumentacja techniczna (adresacja, VLAN-y, ACL, itp.) |
| `pkt/`         | Pliki Cisco Packet Tracer |
| `configs/`     | Konfiguracje urządzeń Cisco |
| `scripts/`     | Skrypty pomocnicze (np. generowanie planu adresacji) |
| `README.md`    | Główny opis projektu |
| `.gitignore`   | Wykluczenia Git |
| `LICENSE`      | Licencja (np. MIT) |

---

## 🧪 Wymagania

- Cisco Packet Tracer `>=8.2.2`
- Wiedza z zakresu: VLAN, routing, DHCP, ACL, bezpieczeństwo sieci

---

## 🛠️ Jak uruchomić projekt?

1. Otwórz `pkt/final-project.pkt` w Cisco Packet Tracer
2. Zweryfikuj działanie VLAN i połączeń międzyoddziałowych
3. Przetestuj ACL z perspektywy Biura IT
4. Przeglądaj konfiguracje z `configs/`

---

## 🧾 Licencja

Ten projekt jest objęty licencją MIT. Zobacz [LICENSE](LICENSE), aby uzyskać więcej informacji.

---

## 🤝 Autor

**Imię i nazwisko**  
Inżynier sieci i student cyberbezpieczeństwa  
📫 kontakt@example.com  
🌐 [Twoje portfolio lub LinkedIn](https://...)

Plan rozbudowy projektu – kolejność wdrażania po zakończeniu podstaw

🔹 Etap 1 – Zabezpieczenia wewnętrzne

✅ 1. ACL na routerze – izolacja między biurami
Tylko VLAN 50 (IT) ma dostęp do wszystkich VLAN.

Pozostałe VLAN-y nie widzą się nawzajem.

Dostęp do VLAN 120 (ZASOBY) tylko z wybranych VLAN.

✅ 2. Serwery lokalne dla biur (zasoby dostępne tylko lokalnie)
Każde biuro otrzyma własny serwer (HTTP, FTP, itp.).

Dostęp tylko z własnego VLAN – blokada międzybiurowa za pomocą ACL.

✅ 3. DHCP i DNS
Centralny serwer DHCP i DNS w VLAN 120.

Automatyczne przydzielanie IP dla komputerów.

DNS z symulowanymi nazwami np. serwer_szefow.local.

🔹 Etap 2 – Zabezpieczenia fizyczne i logiczne

✅ 4. Port Security
Ograniczenie liczby urządzeń na port.

Blokada nieautoryzowanych MAC.

Sticky MAC + shutdown przy naruszeniu.

✅ 5. Wyłączenie nieużywanych portów + VLAN 999 jako czarny VLAN
Nieużywane porty → shutdown.

Przypisanie do VLAN 999, aby nie uczestniczyły w produkcyjnej sieci.

🔹 Etap 3 – Monitoring i symulacja zagrożeń

✅ 6. Honeypot (symulowany serwer przynęta)
Serwer z otwartymi usługami w osobnym VLAN (np. 200).

ACL blokujące dostęp z sieci wewnętrznych poza IT.

✅ 7. Simulation Mode jako narzędzie do analizy ataków
Przechwytywanie pakietów do honeypota.

Obserwacja nieautoryzowanych prób dostępu.

🔹 Etap 4 – Bezpieczne zarządzanie

✅ 8. Zamiana Telnet na SSH
Włączenie SSH na routerze i switchach.

Generacja kluczy RSA, ustawienie użytkowników.

🔹 Etap 5 – Firewall + DMZ

✅ 9. Dodanie Cisco ASA 5505 jako firewalla
Trzy strefy: inside, outside, dmz.

Konfiguracja NAT, reguł dostępu, inspekcji stanu.

✅ 10. Wydzielenie DMZ z serwerami (FTP, WWW)
Dostęp tylko z Internetu lub VLAN 50.

ACL ograniczające połączenia zwrotne.

🔹 Etap 6 – QoS i VoIP (opcjonalnie)

✅ 11. Dodanie telefonów IP i Call Manager Express
VLAN Voice.

QoS priorytety dla ruchu głosowego.



