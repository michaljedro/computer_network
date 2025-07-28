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

