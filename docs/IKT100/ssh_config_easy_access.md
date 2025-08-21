# Oppsett for lett pålogging til kjente ssh-servere

## SSH Config
For å gjøre det enklere å logge inn på kjente SSH-servere, kan du bruke en SSH-konfigurasjonsfil. Denne filen lar deg spesifisere aliaser for servere, slik at du slipper å skrive hele kommandoen hver gang.

### Oppretting av SSH-konfigurasjonsfil
1. Åpne terminalen.
2. Naviger til `.ssh`-mappen:
3. ```bash
    cd ~/.ssh
    ```
4. Opprett eller rediger filen `config`:
5. ```bash
    nano config
    ```
6. Legg til følgende konfigurasjon for hver server du vil ha enkel tilgang til
7. ```plaintext
    Host ikt100
        HostName 10.225.149.214
        User chrissof
        IdentityFile ~/.ssh/ikt100
    ```
8. Lagre filen og avslutt redigeringsprogrammet (i nano, trykk `CTRL + O` for å lagre og `CTRL + X` for å avslutte).
9. Sørg for at filen har riktige tillatelser:
10. ```bash
    chmod 600 ~/.ssh/config
    ```
11. Nå kan du logge inn på serveren ved å bruke aliaset:
12. ```bash
    ssh ikt100
    ```
13. Dette vil bruke de spesifiserte innstillingene i konfigurasjonsfilen, inkludert brukernavn og identitetsfil.
14. ### Eksempel på flere servere
15. Du kan legge til flere servere i samme fil:
16. ```plaintext
    Host server2
        HostName 127.0.0.1
        User user2
        IdentityFile ~/.ssh/server2_key
    ```
17. Nå kan du enkelt logge inn på `server2` ved å bruke:
18. ```bash
    ssh server2
    ```
19. Dette gjør det mye enklere å administrere flere SSH-forbindelser uten å måtte huske alle detaljene for hver enkelt server.
20. ### Sjekk konfigurasjonen
21. Du kan sjekke at konfigurasjonen fungerer som forventet ved å bruke
22. ```bash
    ssh -v ikt100
    ```
23. Dette vil gi deg detaljert informasjon om tilkoblingen og bekrefte at
24. den riktige konfigurasjonen blir brukt.
25. ### Feilsøking
26. Hvis du opplever problemer med tilkoblingen, kan du sjekke følgende:
27. - Sørg for at `~/.ssh/config`-filen har riktige tillatelser (600).
28. - Kontroller at `IdentityFile`-banen er korrekt og at nøkkelen finnes.
29. - Sjekk at serveren er tilgjengelig og at du har riktig
- brukernavn.
30. - Bruk `ssh -v` for å få mer informasjon om tilkoblingsproblemer.
- ### Oppsummering
- Ved å bruke en SSH-konfigurasjonsfil kan du enkelt administrere tilkoblinger til flere servere uten å måtte huske detaljer som IP-adresser, brukernavn og nøkkelfiler. Dette gjør det mye enklere å jobbe med SSH og forbedrer produktiviteten din.
- ## Ekstra tips
- Du kan også legge til kommentarer i konfigurasjonsfilen ved
- å bruke `#` for å gjøre det lettere å forstå hva hver oppføring er for
- ```plaintext
    # Dette er en kommentar
    Host ikt100
        HostName 10.225.149.214
        User chrissof
        IdentityFile ~/.ssh/ikt100
    ```
- Dette kan være nyttig hvis du har mange servere og trenger å huske hva hver
- enkelt oppføring er for.
- ## Sikkerhet
- Husk at det er viktig å beskytte SSH-nøklene dine. Sørg for
- at de har riktige tillatelser (600) og at du ikke deler dem med
- andre. Hvis du bruker en passordbeskyttet nøkkel, må du også sør- ge for at du har passordet tilgjengelig når du logger inn.
- ## Avslutning
- Ved å følge disse trinnene kan du enkelt sette opp en SSH-konfigurasjonsfil for å forenkle tilkoblingen til kjente SSH-servere. Dette vil spare deg for tid og gjøre det enklere å administrere flere servere. Husk å holde konfigurasjonsfilen sikker og oppdatert for å unngå potensielle sikkerhetsproblemer.
- Hvis du har spørsmål eller trenger hjelp, ikke nøl med å spørre i fellesskapet eller søk etter ressurser på nettet. Lykke til med SSH-konfigurasjonen din!
