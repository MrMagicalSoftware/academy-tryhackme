# academy-tryhackme





## Fasi dell' hacking 




**Ricognizione:**
        Questa è la fase iniziale in cui l'hacker raccoglie informazioni sul target. Può includere la ricognizione passiva (analisi di dati pubblici) e attiva (scansioni di rete). L'obiettivo è ottenere quante più informazioni possibili su indirizzi IP, domini, servizi in esecuzione e potenziali vulnerabilità.

**Scansione:**
        In questa fase, l'hacker utilizza strumenti per identificare i dispositivi attivi, le porte aperte e i servizi in esecuzione sulla rete. Questo aiuta a mappare la rete e a identificare potenziali punti deboli.

**Accesso:**
        Dopo aver identificato le vulnerabilità, l'hacker tenta di ottenere accesso non autorizzato al sistema. Questo può avvenire attraverso exploit di vulnerabilità, attacchi di forza bruta, phishing o altre tecniche.

**Mantenimento dell'accesso:**
        Una volta ottenuto l'accesso, l'hacker cerca di stabilire un modo per mantenere l'accesso al sistema. Questo può includere l'installazione di backdoor, rootkit o altri strumenti che consentono di rientrare nel sistema anche dopo che è stato ripristinato.

**Esfiltrazione dei dati:**
        In questa fase, l'hacker cerca di rubare dati sensibili o informazioni riservate. Questo può includere dati finanziari, informazioni personali o segreti aziendali.

**Copertura delle tracce:**
        Infine, l'hacker cerca di cancellare o mascherare le proprie tracce per evitare di essere rilevato. Questo può includere la modifica dei log di sistema, l'eliminazione di file o l'uso di tecniche di offuscamento.

**Analisi post-attacco (opzionale):**
        In alcuni casi, l'hacker può anche condurre un'analisi post-attacco per valutare il successo dell'attacco e identificare eventuali aree di miglioramento per attacchi futuri.








### Esercitazione su Passive Reconnaissance
Room Link : https://tryhackme.com/r/room/passiverecon


In ambito cybersecurity, la differenza tra ricognizione attiva e passiva si riferisce a due metodologie utilizzate per raccogliere informazioni su un sistema, 
una rete o un'organizzazione al fine di identificare vulnerabilità e potenziali punti di attacco.


1. **Ricognizione Passiva**: 
   - La ricognizione passiva implica la raccolta di informazioni senza interagire direttamente con il target. Questo può includere l'analisi di dati pubblicamente disponibili, come:
     - Siti web aziendali
     - Profili sui social media
     - Registri DNS
     - Documenti pubblici (ad esempio, rapporti annuali, white paper)
   - L'obiettivo è raccogliere quante più informazioni possibili senza attirare l'attenzione del target. Questo approccio è utile per costruire un profilo dettagliato dell'organizzazione e delle sue infrastrutture senza rischiare di essere rilevati.

2. **Ricognizione Attiva**: 
   - La ricognizione attiva, al contrario, comporta l'interazione diretta con il target per raccogliere informazioni. Questo può includere:
     - Scansioni di rete (ad esempio, utilizzando strumenti come Nmap)
     - Ping e traceroute per identificare dispositivi e percorsi di rete
     - Interrogazione di servizi per ottenere informazioni su porte aperte e servizi in esecuzione
   - Questo approccio è più invasivo e può facilmente essere rilevato da sistemi di sicurezza, come intrusion detection systems (IDS). Tuttavia, fornisce informazioni più dettagliate e specifiche sulle vulnerabilità e sulla configurazione della rete.


**Comandi utili** <br><br>
whois to query WHOIS servers <br>
nslookup to query DNS servers <br>
dig to query DNS servers<br>





Siti utili  : 

**shodan** <br>
https://www.shodan.io/

![Screenshot 2024-11-04 alle 15 05 24](https://github.com/user-attachments/assets/5053db36-ad21-40f9-b6df-307fe8a874f6)



**dns dumpster** <br>

https://dnsdumpster.com/

![Screenshot 2024-11-04 alle 15 09 20](https://github.com/user-attachments/assets/805a40fb-595a-4027-bb6a-c6ab9bcd46a3)




```
nslookup -type=A tryhackme.com 1.1.1.1
```
I recod disponibili sono : A , AAAA , MX , TXT , SOA , CNAME


**tabella riassuntiva**


![Screenshot 2024-11-04 alle 15 17 28](https://github.com/user-attachments/assets/84775497-0d30-4ab2-a2fe-e46dab91df75)


---

## Obiettivi
1. Comprendere il funzionamento di base di `nslookup`, `dig`, e `whois`.
2. Imparare a raccogliere informazioni DNS e di registrazione di un dominio.
3. Acquisire la capacità di interpretare i risultati di ciascun comando.

---

### 1. `nslookup`
`nslookup` è un comando usato per interrogare i server DNS e ottenere informazioni sui nomi di dominio e i relativi indirizzi IP.

**Esercizi**

- **Esercizio 1.1**: Utilizza `nslookup` per trovare l'indirizzo IP associato a un dominio.
 ```
  nslookup www.google.com
  ```


  **Domanda**: Qual è l'indirizzo IP restituito? Questo IP può cambiare nel tempo? Perché?

- **Esercizio 1.2**: Usa `nslookup` per interrogare un DNS specifico.

 
 ```
  nslookup www.google.com 8.8.8.8
```


  **Domanda**: Quale differenza trovi nel risultato rispetto al DNS predefinito?



**Esercizio 1.3**: Ottieni i server di posta (record MX) per un dominio.
```
  nslookup -query=mx gmail.com
```


**Domanda**: Qual è la priorità dei server di posta restituiti? Qual è la logica dietro la presenza di più server MX?



### 2. `dig`
`dig` (Domain Information Groper) è uno strumento avanzato per interrogare DNS, utile per avere informazioni dettagliate sui record di un dominio.

**Esercizi**

- **Esercizio 2.1**: Utilizza `dig` per ottenere informazioni di base su un dominio.
```
  dig www.google.com
```
  **Domanda**: Quali informazioni aggiuntive rispetto a `nslookup` puoi vedere?

- **Esercizio 2.2**: Esegui una query su specifici record DNS (A, MX, TXT).
```
  dig google.com A
  dig google.com MX
  dig google.com TXT
 ```
  **Domanda**: Cosa rappresentano i record `A`, `MX` e `TXT`? Come sono utili?

- **Esercizio 2.3**: Usa `dig` per interrogare record NS di un dominio.
 ```
  dig google.com NS
 ```
  **Domanda**: Quali server DNS sono autoritativi per il dominio?

- **Esercizio 2.4**: Fai una query inversa (reverse lookup) per ottenere il nome di dominio da un indirizzo IP.
 ```
  dig -x 8.8.8.8
```
  **Domanda**: Che risultato ottieni? Perché il reverse lookup potrebbe essere utile?

---

### 3. `whois`
`whois` è un comando che restituisce informazioni di registrazione su un dominio o un indirizzo IP, come il proprietario, la data di scadenza, ecc.

**Esercizi**

- **Esercizio 3.1**: Usa `whois` per ottenere le informazioni di registrazione di un dominio.
 
  whois google.com

  **Domanda**: Quali informazioni riguardanti il dominio puoi vedere (registrante, date di creazione e scadenza, ecc.)?

- **Esercizio 3.2**: Analizza le informazioni sugli IP.
  
  whois 8.8.8.8
 
**Domanda**: Chi è il proprietario dell’indirizzo IP? Come viene indicata la rete a cui appartiene?

- **Esercizio 3.3**: Verifica un dominio che appartiene a un’azienda o a un'organizzazione meno conosciuta.

  whois openai.com

  **Domanda**: Quali differenze trovi rispetto a un dominio di grandi aziende? Esistono delle restrizioni o delle differenze di privacy?









______________________




# Active Reconnaissance







_______________________



# Comandi Linux : 
https://linux.die.net/man/

![Screenshot 2024-11-07 alle 16 40 59](https://github.com/user-attachments/assets/d60303c7-6115-47c1-9d27-2c5a65592995)



**Switching users**

Switching between users on a Linux install is easy work thanks to the su command. U
nless you are the root user (or using root permissions through sudo), then you are required to know two things to facilitate this transition of user accounts:

The user we wish to switch to
The user's password




```
su
```



__________________________




# Vulnerability Scanner Overview



Imagine you are living in a small, lovely house. One day, you notice that your roof has many small holes. If not treated, these small holes can cause significant problems. During rain, water can come through these leaks and damage your furniture. Dust particles and insects can enter the house through these tiny holes. These small holes are a weakness in your home that can lead to significant problems in the future if not addressed timely. These weaknesses are known as Vulnerabilities. You start repairing the roof to fix this problem and keep your home safe. This process of fixing the vulnerabilities is known as Patching.

Digital devices also have vulnerabilities inside their software or hardware. These are the weaknesses in the software programs or hardware that an attacker can leverage to compromise the digital device. These vulnerabilities may sound normal to you, like the small holes in the roof of a house that can be repaired anytime. However, the vulnerabilities in digital devices can lead to massive damage if not noticed on time. Hackers are always searching for these weaknesses as they make their way to your systems or networks by exploiting them. The interesting thing about digital device vulnerabilities is that you cannot notice them as easily as the holes in the roof until you dedicate yourself to hunting them down. After hunting these vulnerabilities down, the process of patching starts, where fixes are applied to protect the vulnerabilities.








Vulnerability scanning is the inspection of digital systems to find weaknesses. Organizations carry critical information in their digital infrastructure. They must regularly scan their systems and networks for vulnerabilities, as attackers can leverage these vulnerabilities to compromise their digital infrastructure, resulting in a considerable loss. Vulnerability scanning is also an important compliance requirement of many regulatory bodies. Some security standards advise performing vulnerability scanning quarterly, while some advise performing it once a year.

We saw how important it is to conduct vulnerability scans in your digital landscape regularly; however, manually looking for these weaknesses can be very hectic and miss some major ones. The bigger the network is, the slower the process of manual vulnerability scanning would be. This is no longer an issue as some efficient vulnerability scanners that perform automated vulnerability scanning are available in the market. This automated vulnerability scanning has made life much easier. You only need to install the tool and give it an IP address for a host or a network range for a network; it will start checking vulnerabilities and give you an easy-to-read report with the details of the vulnerabilities found.

After identifying vulnerabilities, organizations fix them by making changes to a software program or system. These changes are referred to as Patches.

Vulnerability scans can be categorized into many types; however, the major categorization of these scans are explained below:
Authenticated vs. Unauthenticated Scans

Authenticated scans require the subject host's credentials and are more detailed than unauthenticated scans. These types of scans are helpful for discovering the threat surface within the host. However, unauthenticated scans are conducted without providing any credentials of the subject host. These scans help identify the threat surface from outside the host.



![Screenshot 2024-11-14 alle 14 14 45](https://github.com/user-attachments/assets/bb325d3f-e085-417d-9d1d-d36a81cd1871)


![Screenshot 2024-11-14 alle 14 18 06](https://github.com/user-attachments/assets/ba2a8d22-8bff-4409-a525-7d67d28c3c63)




The choice between vulnerability scan types depends on several factors. Authenticated scans are often used for internal vulnerability scanning, while unauthenticated scans are mostly used for external vulnerability scanning.


## tools

There are many tools available for performing automated vulnerability scanning, each offering unique features. Let’s discuss some of the widely used vulnerability scanners.
Nessus

Nessus was developed as an open-source project in 1998. It was later acquired by Tenable in 2005 and became proprietary software. It has extensive vulnerability scanning options and is widely used by large enterprises. It is available in both free and paid versions. The free version offers a limited number of scan features. In contrast, its commercial version offers advanced scanning features, unlimited scans, and professional support. Nessus needs to be deployed and managed on-premises.


Qualys

Qualys was developed in 1999 as a subscription-based vulnerability management solution. Along with continuous vulnerability scanning, it provides compliance checks and asset management. It automatically alerts on the vulnerabilities found during continuous monitoring. The best thing about Qualys is that it is a cloud-based platform, which means there is no extra cost or effort to keep it up and running on our physical hardware and manage it.


Nexpose

Nexpose was developed by Rapid7 in 2005 as a subscription-based vulnerability management solution. It continuously discovers new assets in the network and performs vulnerability scans on them. It gives vulnerability risk scores depending on the asset value and the vulnerability’s impact. It also provides compliance checks against various standards. Nexpose offers both on-premises and hybrid (cloud and on-premises) deployment modes.


OpenVAS (Open Vulnerability Assessment System)

OpenVAS is an open-source vulnerability assessment solution developed by Greenbone Security. It offers basic features with known vulnerabilities scanned through its database. It is less extensive than commercial tools; however, it gives you the flavor of a complete vulnerability scanner. It is beneficial for small organizations and individual systems. The next section will explore this tool in more detail by performing vulnerability scanning.



Almost all vulnerability scanners offer reporting capabilities. They generate a detailed report after every vulnerability scan. These reports contain a list of the vulnerabilities discovered, their risk scores, and detailed descriptions. Some vulnerability scanners offer advanced reporting capabilities that provide remediation methods for all the discovered vulnerabilities and allow you to export these vulnerability assessment reports in different formats.

Each of the tools mentioned above has its strengths. When choosing a suitable vulnerability scanner for your digital assets, you must consider the scope, resources, depth of analysis, and other factors.


## CVE & CVSS



Imagine yourself as the person sitting on the help desk of an IT complaint office managing many clients. You deal with hundreds of complaints daily regarding IT outages or several other problems requiring support from your company. Let’s see how CVE and CVSS help you track all these inquiries and complaints.
CVE

CVE stands for Common Vulnerabilities and Exposures. Consider CVE a unique number for each of your inquiries and complaints. If there is any update to any issue, you can easily follow up on that using the unique CVE number. Coming out of the help desk example scenario, this CVE number is a unique number given to vulnerabilities. This was developed by the MITRE Corporation. Whenever a new vulnerability is discovered in any software application, it is given a unique CVE number as a reference and published online in a CVE database. This publication aims to make people aware of these vulnerabilities so they can apply protective measures to remediate them. You can find the details of any previously discovered vulnerability in the CVE database. An example of a CVE number given to a vulnerability can be seen in the picture below:


![Screenshot 2024-11-14 alle 14 21 15](https://github.com/user-attachments/assets/96f1a9e5-2d4d-4e18-a427-8f8751f40cc9)






