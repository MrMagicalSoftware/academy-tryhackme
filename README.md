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
  ```
  whois google.com
```
  **Domanda**: Quali informazioni riguardanti il dominio puoi vedere (registrante, date di creazione e scadenza, ecc.)?

- **Esercizio 3.2**: Analizza le informazioni sugli IP.
  ```
  whois 8.8.8.8
  ```
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

Switching between users on a Linux install is easy work thanks to the su command. Unless you are the root user (or using root permissions through sudo), then you are required to know two things to facilitate this transition of user accounts:

    The user we wish to switch to
    The user's password

```
su
```






