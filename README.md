# 🛡️ Reconnaissance Réseau & Évaluation des Vulnérabilités (Semaine 2)

Reconnaissance passive et active complète de la cible `networkwalks.com` et cartographie du réseau local.

## 📌 Aperçu du Projet
Ce projet se concentre sur l'exécution de techniques de reconnaissance active et passive à l'aide des outils natifs de Kali Linux, du scan réseau Zenmap et des opérateurs du Google Hacking Database (GHDB) afin d'évaluer la surface d'attaque de la cible en toute sécurité.

---

## 🛠️ Module 1: Reconnaissance CLI (W2-PM1)
Exécution de 6 commandes essentielles de reconnaissance contre `networkwalks.com` :

* **WHOIS (`whois networkwalks.com`) :** Domaine enregistré via GoDaddy, hébergé sur les serveurs de noms HostGator (`NS6135.HOSTGATOR.COM`).
* **WhatWeb (`whatweb networkwalks.com`) :** Identification du serveur web Apache, CMS WordPress, Bootstrap 7.1.4 et jQuery 3.7.1.
* **NSLookup (`nslookup networkwalks.com`) :** Résolution du domaine cible vers l'adresse IP `192.232.216.135` via le DNS `8.8.8.8`.
* **Curl (`curl -I https://networkwalks.com`) :** En-têtes HTTP/2 200 OK récupérés, API REST active (`/wp-json/`) et en-têtes de mise en cache Nginx.
* **Wafw00f (`wafw00f networkwalks.com`) :** Détection réussie du Pare-feu Applicatif Web (WAF) : **ModSecurity (SpiderLabs) WAF**.
* **DNSRecon (`dnsrecon -d networkwalks.com`) :** Extraction des enregistrements SOA, serveurs de messagerie MX, règles SPF et enregistrements de service SRV cPanel.

*(Voir les captures ci-dessus)*

---

## 🌐 Module 2: Découverte Réseau avec Zenmap (W2-PM5)
Scan du réseau local via l'interface graphique Zenmap sous l'environnement hôte Windows :

* **Adresse IP hôte :** `10.20.142.215`
* **Sous-réseau scanné :** `10.20.142.0/24`
* **Commande exécutée :** `nmap -sn 10.20.142.0/24` (Ping Scan)
* **Résultats :** 1 hôte actif identifié (`10.20.142.215`). Carte de topologie générée et exportée sous `Zenmap1.pdf`.

<img width="960" height="1072" alt="Zenmap" src="https://github.com/user-attachments/assets/74349094-81d7-4824-aac0-0b412ab6c712" />

---

## 🔍 Module 3: Google Hacking & OSINT (W2-PM2)
Reconnaissance à l'aide des dorks Google avancés et de la base GHDB :

1. **Interfaces Admin (`site:networkwalks.com inurl:admin OR inurl:login`) :** 0 résultat (Aucun portail d'administration public exposé).
2. **Documents Exposés (`site:networkwalks.com filetype:pdf`) :** 4 ressources PDF publiques identifiées (Cheat Sheets ARP & SNMP).
3. **Listage de Répertoire (`site:networkwalks.com intitle:"index of"`) :** 0 résultat (Indexation des répertoires désactivée).
4. **Logs / Sauvegardes Sensibles (`site:networkwalks.com ext:log OR ext:sql`) :** 0 résultat (Aucune fuite de sauvegarde détectée).
5. **Exploration GHDB :** Navigation dans le dépôt Exploit-DB GHDB ciblant les catégories de serveurs vulnérables.

*(voir image_Module3)*

---

## 🔧 Dépannage & Résolution
* **Erreur de Résolution DNS (`wafw00f`) :** Erreur temporaire `NameResolutionError` rencontrée lors de l'exécution de Wafw00f en raison d'une réinitialisation éphémère de la carte réseau.
* **Résolution :** Exécution de la commande relancée après stabilisation de la connexion, confirmant avec succès la présence du WAF ModSecurity.
