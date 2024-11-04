# academy-tryhackme





## Fasi dell' hacking 




    Ricognizione:
        Questa è la fase iniziale in cui l'hacker raccoglie informazioni sul target. Può includere la ricognizione passiva (analisi di dati pubblici) e attiva (scansioni di rete). L'obiettivo è ottenere quante più informazioni possibili su indirizzi IP, domini, servizi in esecuzione e potenziali vulnerabilità.

    Scansione:
        In questa fase, l'hacker utilizza strumenti per identificare i dispositivi attivi, le porte aperte e i servizi in esecuzione sulla rete. Questo aiuta a mappare la rete e a identificare potenziali punti deboli.

    Accesso:
        Dopo aver identificato le vulnerabilità, l'hacker tenta di ottenere accesso non autorizzato al sistema. Questo può avvenire attraverso exploit di vulnerabilità, attacchi di forza bruta, phishing o altre tecniche.

    Mantenimento dell'accesso:
        Una volta ottenuto l'accesso, l'hacker cerca di stabilire un modo per mantenere l'accesso al sistema. Questo può includere l'installazione di backdoor, rootkit o altri strumenti che consentono di rientrare nel sistema anche dopo che è stato ripristinato.

    Esfiltrazione dei dati:
        In questa fase, l'hacker cerca di rubare dati sensibili o informazioni riservate. Questo può includere dati finanziari, informazioni personali o segreti aziendali.

    Copertura delle tracce:
        Infine, l'hacker cerca di cancellare o mascherare le proprie tracce per evitare di essere rilevato. Questo può includere la modifica dei log di sistema, l'eliminazione di file o l'uso di tecniche di offuscamento.

    Analisi post-attacco (opzionale):
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


______________________




# Active Reconnaissance













