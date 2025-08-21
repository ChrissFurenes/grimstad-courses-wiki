# Oppsett for lett pålogging til kjente ssh-servere med alias

## SSH Config
For å gjøre det enklere å logge inn på kjente SSH-servere, kan du bruke en SSH-konfigurasjonsfil. Denne filen lar deg spesifisere aliaser for servere, slik at du slipper å skrive hele kommandoen og ip adressen hver gang.

### Oppretting av SSH-konfigurasjonsfil
#### 1. opprette ``config`` filen
i mappen ``.ssh`` som ligger under bruker mappen din. Inni denne mappen lager du en fil med navnet `config`.
##### __Windows__
``C:\Users\<brukernavn>\.ssh\config``
##### __Linux__ og __MacOS__
``~/.ssh/config`` eller ``/home/<brukernavn>/.ssh/config``

#### 2. Legg til konfigurasjon
I filen `config` kan du legge til konfigurasjon for hver server du ønsker
å koble til. Her er et eksempel på konfigurasjon:

```
Host ikt100                     # Dette er aliaset du bruker for å koble til serveren
    HostName 10.225.149.214     # IP-adressen til serveren
    User chrissof               # Brukernavnet du bruker for å logge inn
    IdentityFile ~/.ssh/ikt100  # Stien til din private nøkkel 
    
# NB windows brukere må bruke \ til å navigere i mapper
```

### legge til hostnavn i lokal maskin sin DNS
#### For __Windows__:
1. Åpne Notisblokk som __administrator__ og trykk ctrl + O for å åpne en fil.
2. Gå til `C:\Windows\System32\drivers\etc\hosts`. Husk at du må velge __"Alle filer"__ i filtypevelgeren for å se `hosts`-filen.
3. Legg til følgende linje nederst i filen:
```
10.225.149.214 ikt100
```
4. Lagre filen.

#### For __Linux__ og __MacOS__:
Åpne terminalen og kjør kommandoen:
   ```bash
   echo "10.225.149.214 ikt100" | sudo tee -a /etc/hosts
   ```

