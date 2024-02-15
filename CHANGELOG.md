# Changelog
All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog(https://keepachangelog.com/en/1.0.0/), and this project adheres to Calendar Versioning(https://calver.org/).

<details>

<summary> Template </summary>

## Version

### Added
- New features

### Changed
- Changed behaviour

### Fixed
- Fixed bugs

### Caveat
- Things to take note off

### Security
- Security related fixes

### Deprecated
- Removed features

</details>

## 2024.2.3
### Added
- DHCP relay agent f�r extern accessport adderas vid behov
### Fixed
- Line send delay saknades f�r cmd
- WaitForString i samband med CMD hanterades felaktigt p� grund av bug

## 2024.2.2
### Fixed
- Problem med referens till filnamn f�r byggnadsregistret i settings.json
- Payload felaktig vid discovery i Solarwinds p� grund av felaktig placering av ny funktion

## 2024.2.1
### Added
- St�d f�r SecureCRT 9.5
- Check_web_server har snabbats upp
- Uppslag i byggnadsregistret g�rs om
- Ny namnstandard f�r hostname
- N�r �ldern p� ett l�senord f�r ett AD-konto i Passbolt n�rmar sig 30 dagar innan tvingande byte, kommer anv�ndaren bli uppmanad en g�ng per dag tills det �r bytt.
- Det g�r nu att l�gga till endpoints utan att de tidigare har anslutit till n�tverket
- Varning om en ny nod i Solarwinds finns i ignore list
- Ny funktion f�r backup av delade resurser i Passbolt
### Fixed
- Unpluggable sattes fel p� accessportar (10-15)
- Anv�ndningen av User-Agent var inkonsekvent och delvis felaktig mot RFC
- Avslut av session vid fel mot Passbolt hanterades inte
- Ut�kad loggning vid borttagning fr�n Solarwinds
- Slutade hantera serieportar n�r en ogiltig port p�tr�ffades
- PID och VID f�r Ciscos USB-adapter presenteras inte l�ngre av Windows
### Changed
- "Remove node�" omd�pt till "Delete node�"
- Copyright borttagen d� den inte kr�vs sedan �r 2000

## 2023.10.2
### Added
- St�d f�r RESTCONF
- Verifiering av anv�ndardata fr�n Passbolt
### Fixed
- Loop n�r enhet l�ggs till f�r �vervakning i DNA-Center
- Energywise p� enheter utan support f�r det felar
- R�ttat delar av koden f�r Passbolt efter designfilosofin
- Fel vid generering av csr
- Flera fel vid generering av pfx
- Efter byte av namn i alternativ fem, misslyckas inloggning d� location inte blir korrekt satt
### Security
- �kad s�kerhet f�r NETCONF-YANG
- �kad separation av anv�ndningen av variabeln secret

## 2023.10.1
### Added
- Tar bort backup av SecureCRT d� den kr�ver en mer avancerad hantering �n vad som �r v�rt besv�ret
- Optimerat koden f�r integrationen med Passbolt
- St�d f�r Catalyst 9300-24U
### Fixed
- Hade missat att l�gga till Passbolt f�r alternativ 43
- Kunde f� ett fel n�r install remove inactive �r klar d� raden klipptes n�r systemet v�ntade
- Source interface kunde inte s�ttas korrekt f�r ip http client
- Krasch n�r fel l�senord h�mtades fr�n Passbolt f�r Powershell
### Security
- H�gre och konfigurerbar s�kerhet vid anv�ndning av Powershell

## 2023.9.4
### Added
- Minskat exponeringen av inloggningsuppgifter mellan moduler
- G�r nu att anv�nda range f�r interfacekonfiguration
### Fixed
- Vissa tecken i l�senordet f�r en SSH-session f�r SecureCRT att stoppa scriptet
- Saknat undantag vid retry i requests
- Felstavning i alternativ 3 skapade en krasch

## 2023.9.3
### Fixed
- Missade installation av modulen pgpy
- sol_delete_node kunde krascha n�r nod tas bort i Solarwinds som redan �r borttagen
- Fanns en risk att passphrase f�r Passbolt kunde sparas av misstag
- Autenticeringsfel i requests orsakade en krasch
- Fel l�senord i Passbolt orsakade en krasch
- Problem att skapa SSH-sessioner n�r l�senorden �r f�r komplexa p� grund av specialtecken

## 2023.9.2
### Added
- Rensat bort v�rden som baseras p� grupptillh�righet
### Fixed
- Backup misslyckades d� "Single Instance" inte kunde s�ttas

## 2023.9.1
### Added
- Ist�llet f�r att hantera en krypterad fil med nycklar och l�senord, h�mtas dessa numera i en integration med Passbolt
- Ges m�jlighet att ansluta en trunkport n�r enhet l�ggs till f�r �vervakning fr�n alternativ 2
- Anv�nder User ist�llet f�r Device credentials i Solarwinds
- Enheter som l�ggs till f�r monitorering via provisionering, l�ggs till som unmanaged som standard
- Smartlicensiering direkt mot Cisco ist�llet f�r egen satellit
- F�rb�ttrad felhantering i requests
- Requests �r nu mer robust vid tillf�lliga kommunikationsproblem, och f�rs�ker flera g�nger
### Fixed
- Lagt in en timeout ifall crt_connect_cmd inte kan detektera slutf�rt kommando
- Fastnade vid rensning av flash p� IOS-XE
- Bug i SecureCRT kraschar applikation och/eller script efter en ny serie-session
- Fel i alternativ 14 d�r f�rslag inte gavs n�r trunkportar inte fanns
### Caveat
- En bug g�r att script och/eller applikationen kraschar n�r man g�r en unlock p� alla tabar och sedan anv�nder tab-objektet. Detta g�r att det kommando som l�ste upp alla tabar m�ste tas bort. Inneb�r att om en tab �r l�st och scriptet talar med denna, kraschar scriptet med f�rklaringen att taben �r l�st.

## 2023.8.1
### Added
- St�d f�r att l�gga till KBN-enheter i �vervakningen
- Ny och s�krare hantering av beh�righeter
- St�d f�r Python 3.11.
- Alla delar som anv�nder requests delar nu en gemensam funktion f�r detta s� att alla anrop f�r samma egenskaper
- I alternativ 2 detekteras om horizontal stack �r aktivt, och avbryter om s� �r fallet
- Ny struktur f�r object och v�rden i sessioner
- F�r nu en fr�ga efter provisionering ifall switchen skall adderas f�r monitorering
- Tar bort alternativ 99, tar plats och anv�nds inte
- B�ttre felmeddelanden fr�n funktionen check_web_server
### Fixed
- Ett fel i alternativ 3 som l�mnade kvar en l�st tab
- St�dat ett par detaljer som br�t mot designfilosofin f�r scriptet
- Fel i crt_connect_cmd som gjorde att taben st�ngdes i f�rtid och loggen inte inneh�ll information
- Ett fel i alternativ 60 gjorde att det kraschade n�r man avbr�t
- Detekterade inte huvudversion av Python korrekt
- Fel i alternativ 12 r�rande eem script
- Hade missat detektering av os och plattform vid uppdatering av Python
- Nyckelfel vid nedladdning av uppdaterad nyckel
- Get_stack detekterar inte switchar d�r virtual stack m�ste aktiveras korrekt
### Deprecated
- Rar bort st�d f�r 3.9
- Slutar anv�nda OrionSDK till f�rdel f�r den mer generella requests, d� det �r d�ligt uppdaterat och saknar en hel del funktioner
- Tar bort st�d f�r SecureCRT version 9.3
### Changed
- Begr�nsa LLDP p� trunkar och extern accessport. Detta kokar ned tabellen till enbart de enheter som syns p� en lokal accessport

## 2023.5.1
### Added
- Integration med Cisco Firepower Management Center
- B�ttre hantering av fel vid decodning av json-filer
- Ut�kad hantering av ogiltiga vlan n�r KBN-trunk skapas
### Fixed
- Ogiltiga namn i moduler f�r Solarwinds enligt pylint

## 2023.4.4
### Added
- Vid provisionering av ny enhet och ip eller namn redan existerar, tas vlan interface bort och hostnamn rensas
- Alternativ som skapar trunkar gav inget portexempel n�r switchen har en modul f�r trunkar
### Fixed
- Omdefiniering av inbyggd funktion (exit)
- Fick l�ra mig om deepcopy() f�r att fixa ett problem med att l�gga in flera enheter i f�ljd i ISE
### Changed
- Storm-control av multicast �kades till 20% p� access-portar

## 2023.4.3
### Added
- Mall f�r nya enheter i ISE s�tts nu i settings.json
- Nytt alternativ f�r att ansluta serieport med 115200 baud
### Fixed
- Har varit inkonsekvent med hur centrala variabler anv�nds av subfunktioner
- Beskrivning f�r portar som inte skall anv�ndas sattes inte i settings.json
- Funktionen put_personal_settings anv�nde fel kodtabell
- Meny 20 hade fel ikon i dialogrutorna

## 2023.4.2
### Added
- Funktionen cisco_encrypt anv�nder nu modulen hashlib ist�llet f�r scrypt, som utg�r
- Snabbat upp skrift till sk�rm genom att inte l�ssa sessions-config varje g�ng funktionen crt_sendline anropas
- Huvudet i menyn byggs nu helt dynamiskt d� cli och gui har olika spacing f�r tecken
- Tagit bort dialog n�r session st�nger eller kopplar ned
### Fixed
- Fel i verifiering av servrar i alternativ 3
- Cisco_encrypt visade sig formatera Cisco typ 8 och 9 nycklar felaktigt
### Deprecated
- St�d f�r SecureCRT version 9.2 tas bort

## 2023.4.1
### Fixed
- Tv� fel fr�n tidigare version r�ttade
- Fel i alternativ 40 gjorde att dialogen loopade n�r ett fel intr�ffade
- Funktionen f�r addering av vlan rensade inte skr�ptecken i listan
- Ett fel i uppgraderingsmodulen p�verkade ISL-kompatibla enheter. Anv�nder numera port_trunk f�r att skapa en trunkport
- Funktionen f�r namnbyte blev aldrig riktigt synlig n�r den lanserades. Fixade detta samt verifiering av nytt hostnamn i funktionen

## 2023.3.2
### Added
- Aktiverar DOM monitoring p� modeller som st�djer detta
- St�d f�r USB adaptrar fr�n SiLabs
- St�d f�r C9200CX
### Fixed
- Tar bort kontroll av confreg, d� det v�rdet kan visas intermittent 
- 1000-switchar har en annan syntax f�r jumboframes
- I sol_update_custom fanns ett unikt v�rde som flyttades till settings
- Tagit bort stack-oid som separat v�rde, det �r en effekt av stackwise
- St�d f�r Netconf enbart f�r IOS-XE

## 2023.3.1
### Added
- Statusmeddelanden till cli f�r flera av kontrollfunktionerna
- N�tverksmoduler i switchar h�mtas nu fr�n models.json ist�llet f�r i koden
### Fixed
- Fel i menyn i alternativ 20 �tg�rdat
- Gl�mt att migrera snmp contact till settings.json
- SNMP contact fanns dubbelt
### Deprecated
- Tar bort st�d f�r Python 3.10 d� en modul inte st�djer detta

## 2023.2.3
### Added
- B�ttre felmeddelanden f�r seriesessioner

## 2023.2.2
### Added
- Lagt in ett tidigare separat verktyg
- Menyn f�r alternativ 20 byggs nu p� samma s�tt som huvudmenyn
- Funktioner f�r utf�rdande och hantering av certifikat �r nu tillagda
- Verifierar configuration register i alternativ 2 och 9
- Kan nu manuellt ange ip eller acceptera f�rvald adress i alternativ 2
- Tagit bort on�diga loopar, och likriktat anv�ndningen av get_model
### Fixed
- Fel vid uppgradering av IOS-XE skapade o�ndlig loop
- �teranv�ndning av �ppna flikar med seriesessioner kunde fallera i vissa fall
- Kontroll av antalet serieportar skall bara kontrollera godk�nda adaptrar fr�n listan
### Changed
- Reload sker nu sist i alternativ 2
### Security
- Mitigerar CVE-2023-20076

## 2023.2.1
### Added
- Uppgradering bryts ut som en funktion som kan �teranv�ndas, detta minskar komplexiteten
- Menyn bryts ut som en funktion f�r att kunna �teranv�ndas i andra script
- Felmeddelande om f�r m�nga USB-adaptrar �r anslutna (>1)
- Uppgradering tar inte l�ngre bort aktiv image
- Gjort en del funktioner som h�mtar in information mer robusta
- Hanterar felaktig USB-seriedrivrutin
### Fixed
- Krasch vid uppdatering av interface ifall Solarwinds inte �r n�bar
- Fel vid prompt f�r �verskrivning av befintlig fel kunde loopa uppgradering
- Felhantering av get_stack hade fallit bort
- "ip routing" finns inte p� IE-3300
- Felhantering vid skapande av seriesession i alternativ 2 har fallit bort

## 2023.1.6
### Added
- Nytt alternativ som sparar aktiv session till Session Manager

## 2023.1.5
### Fixed
- Omsync till DNA-Center misslyckades d� payload var felaktig
- KBN trunk kan inte anv�nda ADD, s� EEM-scriptet m�ste tas bort och l�gga till
- EEM st�ds inte av alla modeller

## 2023.1.4
### Added
- Varning n�r interface uppdateras p� en enhet som inte �r upplagd i Solarwinds, har nu tagits bort
- Nytt alternativ f�r att d�pa om en enhet i alla system, och �ven p� sj�lva enheten via SSH
### Fixed
- Fann ett problem med detektering av viss text i en session, som gjorde skillnad p� SSH och serie-sessioner. Detta inneb�r att samma f�rdr�jning som serie-sessioner har f�r varje tecken, ocks� l�ggs in i SSH- och Local Shell-sessioner.
### Changed
- Ut�kad loggning till buffert
- Slutar logga ntp
- Power budget f�r IE3300 var f�r l�g

## 2023.1.3
### Added
- Alternativ tv� st�nger inte l�nge av sessionen

## 2023.1.2
### Fixed
- (Connection timed out) vid uppgradering
- Tagit bort insamling av output vid Local Shell, detta gav intermittenta problem att avsluta session
### Changed
- Lagt till EEM-script vid provisionering som f�rhindrar vanliga misstag

## 2023.1.1
### Added
- Variablerna username och group s�tts nu via systemenv
- Snabbat upp ssh och serie-sessioner
- Tar bort migreringar av inst�llningar fr�n tidigare versioner
- S�tter diverse inst�llningar f�r emulering och f�rg f�r alla sessioner
### Fixed
- Input dialog saknade strip
- Fel i alternativ 13 som kraschade scriptet p� switch med IOS-XE
- Ibland detekterades inte ett slutf�rt kommando i CMD

## 2.1.7
### Fixed
- Fel vid installation och uppdatering av moduler pga tecken fr�n vissa moduler

## 2.1.6
### Fixed
- Optimerad laddning av externa moduler
### Deprecated
- Modulen python-certifi-win32 supporteras inte l�ngre, byts ut mot pip-system-certs

## 2.1.5
### Fixed
- Hanteringen av serieportar kunde fela i alternativ 40
### Deprecated
- RDP-sessioner via script �r fr�n SecureCRT version 9.4 inte l�ngre supporterat

## 2.1.4
### Added
- Restricted QoS p� accessport f�rsvinner
- Helt gjort om hur stackar hanteras samt r�ttat en del fel p� v�gen
- Lade till global metadata i docstring
- Multigig migreras in i accessport ist�llet
### Fixed
- Ett fel sm�g sig in fr�n f�rra versionen som r�r identifiering av interface i kluster
- �ndrat anv�ndningen av begreppet cluster till stack, betyder olika saker

## 2.1.3
### Added
- St�d f�r NETCONF
- St�d f�r WS-C3560CX-12PD med multigig trunkportar
### Fixed
- Detektering om switch �r ansluten i meny 2 kunde fela ibland
- Screen Sync kunde i vissa fall bli felaktig
- Funktionen get_model kunde krascha ibland av ok�nd anledning

## 2.1.2
### Added
- Uppdatering av moduler kan nu skjutas upp
- Verifiering om en switch �r ansluten sker innan borttagning med val 4
- Flervalsfr�gor har f�tt en ansiktslyftning
### Fixed
- Val 3 tog inte h�nsyn till att description p� port kunde ha olika str�ngar

## 2.1.1
### Added
- F�r en extern accessport g�rs nu �ven en shut/no shut
- Nytt alternativ f�r att rensa en port och markera som FREE
- Aktivera scriptindikator i tab
- Koden bakom menyn formaterar nu automatiskt kolumnerna och h�mtar beskrivning fr�n funktionerna
- Kommer att lansera i en publik version som saknar delar med sekretess
- "Description" p� en port h�mtar nu sitt v�rde fr�n settings.json
- St�d f�r utbyggnadsmodulen IEM-3300-8S
- Vid provisionering verifieras att ingen port �r ansluten
### Fixed
- I meny 11 tas ordet ISE bort d� det inte enbart kunde producera ISE-accessportar
- Smart license transport cslu var felstavat

## 2.10.3
### Added
- S�tter sessionsoptioner f�r RDP
- Hur menyn skapas �r helt omskriven
- N�r en trunkport skapas (intern och mot kbn) g�rs nu en shut/no shut
- Alternativ 13, extern accessport, har f�tt validering av vlan id
- Json-fil f�r vlan inneh�ller nu mer information som anv�nds av olika delar
- Optimerat hur json-filer l�ses in
### Fixed
- N�r portkonfigurationer utf�rs (10-14) g�rs ingen unlock av tab n�r ett fel uppst�r

## 2.10.2
### Added
- M�jlighet till gruppinst�llningar baserat p� inloggad anv�ndare
- Verifiering av inloggad anv�ndare mot lista av godk�nda
### Fixed
- Strukturerat om personalsettings samt migrering
- Avslutar ssh sessioner felaktigt i rapporter och uppgradering n�r ett fel intr�ffar
- Single Instance blev fel vid uppstart
- Krash i rapport 32 om inga multigig-portar finns
- Auth prompt enbart giltigt i ssh-sessioner

## 2.10.1
### Added
- Backup av SecureCRT konfiguration varje m�nad
- N�dv�ndig katalogstruktur skapas om den saknas
- Nya menyalternativ f�r anslutning av SSH och RDP
### Fixed
- Tid som anv�nds i scriptet kunde skilja sig �t i olika delar
- F�rb�ttrad och enhetlig detektering av v�rden i personalsettings
- Misst�nker ett problem vid uppdatering av Python moduler n�r uppl�sningen p� sk�rmen �r d�lig
### Changed
- Device classifier aktiveras nu som standard

## 2.9.5
### Added
- Quickfix avslutas om ett felaktigt kommando p�tr�ffas
- Applicerar protocol NO-OP p� alla SSH-sessioner
- M�jlighet till loggning av alla ssh-sessioner
- Skrivit om hur SSH-sessioner hanteras f�r att g�ra rapporter snabbare genom att �teranv�nda sessioner
- St�d f�r SecureCRT 9.4 (Intern pre beta utv�rdering)
### Changed
- St�ller in h�gsta m�jliga STP prioritet som standard
- Vid konfiguration av KBN trunkport tas den h�ga STP prioriteten bort s� att switch blir root
### Fixed
- Missf�rst�nd med en funktion i API gjorde att en flik d�r script k�rs, fortfarande f�rs�kte st�ngas (fr�n 2022.9.2)
- Inkonsekvent syftning i text och kommentarer

## 2.9.4
### Fixed
- St�dat bort ett par bortgl�mda rader f�r tester
- Funktionen crt_connect_ssh st�dar nu inmatade v�rden fr�n skr�ptecken
- I crt_connect_ssh kunde vissa kommandon detekteras felaktigt s� att scriptet pausade
### Added
- Strukturerat om models.json med en ny hierarkisk struktur f�r samtliga interface
- Ny funktion f�r att skicka kommandon till flera enheter baserat p� externa listor (quickfix)
### Changed
- Smart license har �ndrats, ny konfiguration avspeglar detta

## 2.9.3
### Added
- N�r en trunk- eller access-port skapas s�tts samtidigt unpluggable i Solarwinds

## 2.9.2
### Fixed
- Funktionen ping validerades felaktigt p� ett par st�llen
- �ndrat inkonsekventa svar fr�n vissa funktioner
- Flik d�r script k�rs kan inte st�ngas

## 2.9.1
### Fixed
- Profilnamnet f�r Config Manager blev fel om uppgradering av moduler skedde samtidigt som Config Manager inte aktivt anv�ndes
- F�rtydligat vilket konto som skall anv�ndas f�r DNS
- Saknade verifiering av DNS master innan provisionering och borttagning av enhet

## 2.7.1
### Added
- Ny versionsnumrering som bygger p� datum och ett l�pande versionsnummer
- Verifierar lokal sync av delade filer fr�n Infras teams-kanal
- Optimerat hanteringen av installerade moduler
- Aktiverar automatisk uppdatering (Nyhet i SecureCRT 9.3)
- St�d f�r switchen C9200L-24PXG-4X
- Funktion f�r att f�rhindra timeout p� b�de serie- som ssh-sessioner n�r dialoger l�mnas en l�ngre tid
- St�d f�r Python 3.10
- Koden verifieras nu �ven med Mypy
- St�d f�r multigig i kombination med StackWise
- Sessionernas flik f�r ett namn efter vad de anv�nds till f�r tillf�llet
- St�d f�r alla k�nda Prolific och FTDI chipsets
- Uppdatering av installerad Python
- Optimerat �verf�ringen av uppgifter mellan moduler f�r SSH
- Hantering av idle-timeout i alla sessioner
### Fixed
- Logfil vid provisionering skapas inte korrekt
- Kontroll av kluster kan returnera olika stavning
- Fel encoding vid l�sning av groups.json
- R�ttat koden efter verifiering med Mypy
- "Auto qos global compact" st�ds fr�n 15.2.7
- SNMP location till�ter nu mer kombinationer
- S�tter inst�llning f�r delay i sessioner s� att f�ruts�ttningar i scriptet st�mmer n�r det k�rs
### Deprecated
- Tar bort st�det f�r SecureCRT 9.0 och 9.1
- Tar bort st�d f�r Python 3.8
- Tar bort st�d f�r MacOS, men bibeh�ller m�jlighet att skala till andra os i framtiden

## 2.6.8
### Added
- Alla underfiler till scriptet ligger nu samlade i ett bibliotek
- St�d f�r SecureCRT 9.3
- St�d f�r IE-3300
### Fixed
- Automatiskt inventarienummer felade n�r man angav ett eget, samt st�d f�r test

## 2.6.7
### Added
- Ny funktion f�r manuell uppgradering och verifiering av programvaran i en switch
- Verifiering av inventarienummer s� att det inte �teranv�nds
- N�sta lediga inventarienummer f�resl�s i dialogen, samt verifieras innan den allokeras
### Fixed
- Vid borttagning av switch kan det fela om man anger ip
- ise_delete_device kunde krascha under speciella omst�ndigheter

## 2.6.6
### Fixed
- Hanterar krasch n�r felaktigt anv�ndarnamn anges f�r DNS-server
- Fel uppstod n�r image redan finns p� switch med install mode
- Screen.Synchronous = True tas bort, hj�lpte inte�
- crt_sendline har nu alltid en 175ms f�rdr�jning f�r varje rad. Den dynamiska varianten kan fela ibland troligen pga seriebuffertfel

## 2.6.5
### Added
- Kan startas som ett script med argument via SecureCRT Button Bar, och d� direkt starta ett menyalternativ och avsluta scriptet efter�t
### Fixed
- St�dat bort funktion som gl�mts bort

## 2.6.4
### Added
- Ers�tta funktion som fr�gar sessionsdatabas fr�n ISE med DNA-Center ist�llet. Ger mer och tillf�rlitligare information

## 2.6.3
### Added
- Snabbat p� svar i dialoger d�r man kan v�lja mellan hostnamn och ipadress genom att inte v�nta p� dnsuppslag f�r ip

## 2.6.2
### Added
- Menyalternativ 41 f�rsvinner. Switch anges ist�llet i f�rsta dialogen i menyn

## 2.6.1
### Added
- B�ttre dokumentation i port_trunk
- Nytt menyalternativ som ansluter en switch med ssh
### Fixed
- R�ttat stavfel i kommentarer
- F�rtydligat variabelnamn i put_personal_settings
- Rate-limit f�r API-anrop till DNA-Center

## 2.6.0
### Added
- Snabbat p� installation och uppdatering av moduler vilket minskar antalet omstarter av SecureCRT
- L�gger till switch i DNA-Center
- Tar bort switch i DNA-Center
- F�rb�ttrad hantering av strukturfel i json-filer
- F�renklad hantering av ISE noder i settings.json
- Koden �r verifierad och r�ttad med Pylint
- Strukturerat retur av v�rde och status fr�n funktioner
- About i menyn som tar anv�ndaren till systemdokumentationen
- Verifiering sker av att lokal biblioteksstruktur finns
- De st�llen som anv�nder "sh ip int brie" har f�tt en b�ttre regex-matchning
- Verifiering av att ett certifikat �r betrott sker numera genom en variabel i settings.json
- Screen.Synchronous = True, anv�nds f�r att f�rhindra buffertfel
### Fixed
- Fel variabel anv�ndes i DNS_query n�r man angav ipadress
- Dokumentationen f�r Screen.WaitForString i SecureCRT st�mmer inte, returnerar en integer och inte ett booelskt v�rde som det borde
- Timeout p� API-f�rfr�gningar f�r att inte fastna i en o�ndlig loop
- Funktionen add_vlans f�r felaktig lista med vlan
- Meny 12 har en o�ndlig while-loop
- Funktionen get_cluster gav fel om den inte anv�ndes via ssh
### Changed
- "logging monitor debug"

## 2.5.5
### Added
- De alternativ som g�r, l�ser sessionen n�r scriptet k�rs f�r att undvika oavsiktlig input
- Efter introduktion av DNS kan man nu ange b�de hostname, fqdn och ipadress i dialogerna
	
## 2.5.4
### Added
- Adderar �ven PTR i DNS
- St�dat utseendet p� menyer med input
- L�ser sessionen vid provisionering f�r att f�rhindra oavsiktlig input
### Fixed
- Vissa endpoints skickade inte med all info vilket kraschade scriptet

## 2.5.3
### Added
- Likriktat alla input-dialoger
- Tydligare informationsrutor
- Nya alternativ 30 ger m�jlighet att se var en enhet �r ansluten genom dess mac. Man ges �ven m�jlighet att ansluta till switchen som enheten ansluter till om det sker tr�dat.
### Changed
- aaa accounting update newinfo periodic 15 (�ndrat fr�n 2880 minuter)

## 2.5.2
### Added
- L�gga till och ta bort DNS RR f�r switchens inventarienummer via PowerShell
- ISEFindDeviceByIP returnerar nu �ven hostname om ip existerar
- Input av namn p� site blir striktare f�r att hantera DNSnamn korrekt

## 2.5.1
### Fixed
- Om man l�mnar switchen mer �n 60 minuter med en dialog, kommer exec-timeout g�ra att scriptet fallerar med att komma vidare d� prompten �r �ndrad
- Fel i detektering av tidigare provisionerad switch

## 2.5.0
### Fixed
- F�rb�ttrat och likriktat verifiering av ansluten enhet i ConnectSSH
- Lyckats anv�nda type hints p� ett inkonsekvent s�tt, st�dat detta
- Anv�nt default-v�rden i funktioner i f�r stor utstr�ckning vilket st�ller till det vid fels�kning
- Felet i SerialConnect fr�n 2.4.2 blev aldrig riktigt l�st, blev fel under andra omst�ndigheter ist�llet. Detta �r nu l�st genom att skriva om i stort sett hela funktionen
- St�dat hur s�kv�gar anges i settings.json vilket var inkonsekvent angivet
- CheckExecMode kunde ibland fallera p� �ldre switchar som tog tid p� sig efter f�rsta dialogen
- Ny dialog i CLI hanterades inte av CheckExecMode
- Anv�nder ping ist�llet f�r verifyinternet (som tas bort) d� detta skapade ett moment 22 med kravet p� requests
- Ett fel intr�ffade vid uppgradering av C9300-24S
- Uppt�ckte att seriebuffert fortfarande kunde sl�nga tecken, dock ytterst s�llan. Lade in 25ms f�rdr�jning f�r varje rad i SendLine
- Ett fel kunde intr�ffa vid uppgradering d�r image redan finns p� flashen
### Added
- St�d f�r Credentials Manager n�r SecureCRT version 9.2 anv�nds
- Alternativ 13 l�gger nu till vlanet och namnar det
- F�rb�ttrad felhantering av SSH-sessioner
- Verifiering av modellnummer n�r factory default sker f�r att undvika att fel typ av enheter rensas
- �versyn av funktioner i koden genom enhetlig namning och konsolidering
- Stadsn�t-trunk kan nu inte skapas om man anger vlan som inte finns via stadsn�tet
- S�tter globala inst�llningen "Single Instance" och default session inst�llningen "Auth prompt in windows"
- S�kv�g till lokalt bibliotek f�r SecureCRT s�tts nu i settings.json
- Hashning av nycklar och l�senord innan de skriv till sk�rmen, f�r att �ka s�kerheten vid inmatning och loggning
- Interface som inte anv�nds anges nu i models.json
- St�d f�r multigig-portar som kan ha en helt annorlunda namnstandard
- St�d f�r ny modell WS-C3560CX-8XPD-S och C9200L-24PXG-4X med multigig-portar
- Log med timestamp skapas vid provisionering f�r att f�nga upp eventuella fel
- Detektering av NM p� C9300 �teruppst�r
- Snyggat till header i menyn samt strukturerat listan f�r b�ttre l�sbarhet
- Tagit bort IBNS2, blir om�jligt att underh�lla den koden d� den inte anv�nds skarpt
- SOLFindIP hanterar error 500 fr�n webserver
- Tydligare dialog vid uppgradering n�r kabel skall anslutas eller tas bort
- F�rhindra provisionering av redan provisionerad switch
- N�r man g�r en extern accessport anpassas vissa inst�llningar om det g�ller Lanbit
### Changed
- Version  12.2.55 gillar inte pipe efter "dir flash", byter till "show flash" ist�llet
- Lade till "auto qos global compact" p� utvalda modeller
- Lade till "dot1x timeout tx-period 7" i PortAccess
- Flyttat ISE specifika rader innanf�r villkoren f�r detta
- ISE Syslog till MNT tas bort
- Lade till "transport output none" p� alla line

## 2.4.5
### Fixed
- Problem att detektera serieportar p� nyare datorer, tagit bort notis om osupporterade serieportar
- Tv� fel i tab-objektet vid uppgradering

## 2.4.4
### Fixed
- F�r vissa switchar kunde man inte skapa access eller trunk port om den normalt sett inte skulle ha en s�dan port
### Added
- Kontroll av modul i C9300 tas bort, �r nu standard

## 2.4.3
### Added
- Kan nu l�gga till en bredbandsenhet i ISE

## 2.4.2
### Fixed
- R�ttat fel i inmatning av vlan, vlan mellan 50 och 99 ans�gs ogiltiga
- Fel i uppgraderingen gjorde att en reload aldrig utf�rdes d� en retur saknades
- Fel i funktionen SerialConnect gjorde att fel tab valdes, vilket kunde vara f�r�dande

## 2.4.1
### Added
- St�d f�r SecureCRT 9.2
- Fix i alternativ 20 tas bort, felet avhj�lps genom att g�ra en ny ISE-port ist�llet
- Alternativ 11 och 14 st�nger porten tillf�lligt under konfigurationen

## 2.4.0
### Fixed
- N�r en tab �teranv�ndes blev den inte aktiv
- Optimerat vilka kommandon som skrivs till switchen medans man fortfarande kan avbryta provisioneringen
- Saknade en timeout f�r versionsverifieringen
### Added
- St�d f�r att h�mta adress till SNMP location fr�n byggnadsregister via Excel
- Ny modul som kan �vers�tta svenska tecken
- Verifiering sker att just en switch �r ansluten i aktiv session
- Detekterar om scriptet exekverats i en CMD eller WSL-session, kunde annars fastna i en loop
- Inbyggd managementport s�tts nu fr�n models.json
- N�r ISE inte anv�nds skapas accessportarna, men utan access-vlan
- N�r KBN-trunk skapas, skapas nu �ven alla vlan i databasen och namnas r�tt
- Versionsinformation i JSON-filerna
- Portar f�r API st�lls nu i settings.json
- Alternativet f�r undantag skriver nu om hela portens konfiguration
- Nytt menyalternativ som ansluter alla anslutna serieportar
- Helt omarbetar anslutning med ssh, anv�nder nu SecureCRT ist�llet f�r en modul. Mycket snabbare!
- M�jlighet att detektera StackWise
### Changed
- AccessPort:
  Port-security st�dades
  Authentication event st�dades

## 2.3.7
### Fixed
- En viss typ av switch anv�nder ett anpassat/felaktigt modellnummer p� vissa st�llen, vilket resulterar i att aktiv programversion inte detekteras

## 2.3.6
### Fixed
- Bytt tab mot space enligt PEP-8. Skapade problem i olika editorer
- GetVersion felade ibland och kraschade scriptet, n�r texten inte f�ngades fr�n cli
- Missat att ange domain name och VTP domain i settings.json, ist�llet f�r h�rt i koden
- Exceptions �r nu specifika enligt PEP-8
### Added
- B�ttre hantering och �teranv�ndning av seriesessioner, som redan finns i en tab
- Konsoliderat os-specifika inst�llningar till preChecks
- Settings och secret laddas nu inte i varje modul
- Dialogen runt att ange interfacenamn �r f�rb�ttrad. Exemplet �r en korrekt port f�r den modellen och funktion
### Changed
- "ip domain-lookup" skall numera vara "ip domain lookup"
- Syntax f�r smart token �r �ndrat p� C9K

## 2.3.5
### Added
- St�d f�r install mode f�r utvalda switchar
- St�dat bort funktionen CleanFlash som integreras i �vrig kod ist�llet
- Automatisk omstart av switch efter uppgradering
- L�gger in omstart av SecureCRT efter uppgradering av Pythonmoduler
- Vid uppdatering eller installation av moduler valideras internet�tkomst
- J�mf�r hash av den lokalt lagrade nyckelfilen f�r att avg�ra om den �r �ndrad
### Fixed
- Hanteringen av seriesessioner felar fortfarande, trimmat vilket v�rde den anv�nder f�r utv�rdering av ScriptTab
- Tagit bort kontroll av returncode efter uppgradering via PIP, dessa kan variera trots att de lyckas
- Diverse stavfel i dialoger
### Changed
- autoinstall �r nu disablat som standard
- "ip domain-name" �r �ndrat till "ip domain name"
	
## 2.3.4
### Fixed
- En del mindre anpassningar efter kontakt med supporten hos Vandyke, och dokumentation

## 2.3.3
### Fixed
- F�rb�ttrad hantering av seriesessioner. Kan nu hantera att flera serieadaptrar �r anslutna
- Ett fel uppst�r n�r inga tabbar �r �ppna och scriptet k�rs med alternativ som kr�ver en seriesession, tempor�r l�sning i v�ntan p� �rende

## 2.3.2
### Fixed
- Felaktig hantering n�r usb-adaptern inte �r supporterad/k�nd
- Felaktig hantering n�r ingen usb-adapter �r ansluten
- N�got har h�nt i Windows vilket g�r att vissa adaptrar inte identifierades r�tt. Har �ndrat hur en adapter identifieras

## 2.3.1
### Added
- St�nger numera inte aktuell tab n�r man startar en seriesession
- St�nger seriesessionen efter sig
- Konsoliderade allt r�rande ISE i settingsfilen
- Meny 5 s�tter nu �ven profile id p� utvalda devices
### Fixed
- I meny 5 st�r numera nu macadressen i meddelandet n�r den lyckats och n�r den inte hittat enheten
- Funktionen validatemac var inkonsekvent med vilken datatyp den svarade med
- Tydligare felmeddelanden n�r json-fil inte kan l�sas
- F�rtydligat texten i meny 4
- F�rb�ttrat verifiering av jsondata n�r detta l�ses in
- F�rb�ttrad hantering av seriesessioner
- Felstavning i meny 4 r�ttad
- Meny 14 gjorde en default av porten innan, vilket �r fel
- ConnectSerial returnerade med inkonsekvent datatyp
### Changed
- F�rb�ttrad s�kerhet i ssh

## 2.3.0
### Added
- G�r om hur versionen p� os kontrolleras. St�ndigt fel med denna p� n�got s�tt, s�rskilt med IOS-XE
- Med ny funktion som l�ser version, kan "old_code" tas bort i models-filen
- MAC-validering st�djer nu ett till format: utan avgr�nsare
- St�dat bland funktioner s� att returnerat v�rde har samma format i alla applicerbara funktioner
- Flyttat device-sensor och device-tracker s� att de �ven kommer med om man inte vill ha ISE
- St�d f�r SecureCRT version 9.1
- Automatisk installation och uppdatering av moduler
- St�d f�r personliga inst�llningar som lagras lokalt p� datorn
- F�renklat koden som bygger menyn, var en rest fr�n ett f�rs�k att bygga menyn utifr�n en JSON-fil
- Anpassat settings.json f�r nya menyalternativ sex
- Adderat menyalternativ 21 och 22, tv� olika show kommandon
- Omarbetat hela funktionen GetModel f�r att g�ra den mer robust
- B�rjat anv�nda type hints i koden f�r funktioner
### Fixed
- Missat st�det f�r MacOS p� sistone, lagat detta i de delar som hanterar s�kv�gar och enheter
- R�ttat fel i models.json
- St�dat importerade moduler
- Verifiering av certifikat verifierade fel port i vissa fall
- Regex f�r location till�t inte gatunamn med mellanslag
- Fel versionsinformation f�r vissa switchar i models.json
- St�ngt sessionen efter lyckad validering av certifikat i ValidateCert
- Hantering av undantag (exceptions) i funktioner som l�ser json-filer
	
## 2.2.2
### Fixed
- Fel vid uppgradering n�r flashen redan inneh�ller filen, men inte �r den aktiva
- Fel i accessport gjorde att en rad inte provisionerades i normala fall
- URL f�r nedladdning av secrets-filen var felkonstruerad

## 2.2.1
### Added
- Nu snabbare att skriva kommandon i cli
- Detekterar tidigare provisionerad switch
- Validering av macadress i meny 5
- Smart license �r nu skalbar f�r framtida modeller genom "smartlicense" i models.json
- Management �ver L3 best�ms genom "layer3" i models.json
- Valbart st�d f�r IBNS 2.0, genom "ibns2" i models.json och networks.json (beta)
- Terminalens bredd �ndrad till 150 tecken
- Meny 5 kan nu ta en kommaseparerad lista av macadresser
- F�rfinat hur access och trunkportar selekteras, tagit bort ett modellberoende i koden
- Smart license g�r nu mot egen intern server
### Fixed
- Fixat fel som uppst�r n�r ledigt utrymme p� C9X skall r�knas ut
- Fixat fel i Ping
- C9300-24S har inga accessportar, men scriptet trodde det. �r nu fixat

## 2.2.0
### Added
- Jag har �verarbetat hur menyn byggs, men nu mer programmatiskt korrekt
- Uppgraderingsport tas nu fram dynamiskt ist�llet f�r statiskt fr�n modelno.csv
- All inl�sning av inst�llningar sker numera fr�n JSON-filer
- Verifiering av certifikat sker nu som standard
- Exec-timeout �kas fr�n fem minuter till 15
- Flyttat all modellspecifik information till JSON-fil
- Kontroll av f�rkrav flyttad till egen funktion, som dessutom enbart exekveras vid uppstart
- Selektivt styra per vlan om karant�n, telefoni eller ISE skall anv�ndas i networks.json
- Prefix p� interfacenamn tas numera fr�n models.json
- Alternativ 5, �ndra id grupp f�r endpoint (MAB)
- Vissa "lite"-switchar har en h�rdvarulimitering f�r hur m�nga portar som kan anv�nda exempelvis auto qos. Tar nu h�nsyn till detta med "restrictedqos" i models.json
### Fixed
- Funktionen f�r att rensa flash anv�nde fel variabel och skrev ut skr�ptecken ist�llet. Funnits sedan pre 2.0
- CheckExec kunde fela ibland, lade in en timeout f�r den dialogen och omstart inom loopen
- Alternativ 13, extern accessport, �r n�got uppst�dad f�r bredare anv�ndningsomr�de
- Solarwinds discovery anpassat f�r C9300

## 2.1.1
### Added 
- F�rb�ttrad hantering av PSN-noder 
### Fixed
- Regex f�r verifiering av vlan felar p� nummer som slutar med en nolla, exempelvis 40

## 2.1.0
### Added
- Menyalternativ fyra som tar bort en enhet fr�n Solarwinds och ISE, med validering att enbart en ip f�r accessn�ten v�ljs
- Verifiering av certifikat �r nu modul�r, minskar komplexitet vid nya integrationer
- Uppdaterat matchning av interfacenamn att klara av 100Gb och 200Gb interface, samt st�d f�r Nexus
### Fixed
- Call-home kan fela n�r den namnuppl�ser �ver ipv6 ist�llet f�r ipv4

## 2.0.4
### Added
- Login block vid upprepade inloggningsf�rs�k
- Kr�ver ny modul, python-certifi-win32, som l�ser lokala certifikat i Windows
- Validering av certifikat i integrationen med ISE och Solarwinds
- Verifiering att API svarar korrekt innan menyalternativ exekveras
- Verifiering av installerade moduler
- Validering av vlan, interface och ipadress sker i separat funktion f�r l�ttare underh�ll
### Fixed
- Integrationen mot ISE och Solarwinds anv�nder inte global variabel f�r servernamn l�ngre, n�got som gl�mdes kvar fr�n pre 2.0
- Fel variabel i del av if-sats p� ett par st�llen, gjorde att dialogen inte kunde avslutas med cancel eller X
- Felstavning som p�verkade portskapande f�r 3560CG, felaktig str�ng
- Fel som kraschade scriptet i menyalternativ 10, anv�nde fel variabel
	
## 2.0.3
### Added
- Trunkar blir inte l�ngre unplugged i menyalternativ 3
### Fixed
- Anv�nda Orion SDK f�r IPAM integrationen precis som andra delar som talar med Solarwinds API

## 2.0.2
### Fixed
- Cisco USB-adapter svarar med pid och vid som NoneType, vilket kraschar scriptet
	
## 2.0.1
### Added
- Randomisera ordningen f�r ip till dns, mnt-nod, ntp och psn-nod f�r att "lastbalansera"
- Tagit bort ett par rutor med positiv status som kr�vde interaktivitet i on�dan
- Tagit bort Energywise

## 2.0.0
### Added
- �versatt till Python 3.8
- Menysystem ers�tter de separata scripten
- Factory default och T2KBN �r flyttade till nya menyn
- B�ttre formatering, l�sbarhet och hantering av json-kod i dialogen med REST API
- Kryptering av inneh�llet i l�senordsfilen som nu heter secret.enc. Versionsberoendet kan d�rmed tas bort, och ers�tts med en nyckel som sparas i varje anv�ndares dator genom en dialog om filen saknas
- St�d f�r Catalyst 1000-serien
- H�rdat konfigurationen av IOS baserat p� r�d av Cisco. Bland annat inloggning enbart med SSHv2
- St�dat boolesk hantering
- St�dat hantering av modellspecifik konfiguration
- M�jlighet att addera nya enheter till Solarwinds och s�tta r�tt polling och egenskaper med RESP API
- Tagit bort st�d f�r cisco-phone p� accessport
- St�d f�r KBN3 tas bort
- Ping av enhet f�r verifiering att den �r korrekt ansluten innan provisionering forts�tter
- Skapar automatiskt en session med ansluten serieport n�r det beh�vs. USB adapterns pid och vid m�ste finnas med i tuple tplPID och tplVID. Detta s� att inte fel adapter v�ljs.
- Detekterar nystartad switch och hanterar den dialogen om auto install till priv exec
- Samtlig input har regex verifiering f�r att undvika krasch eller loopar
- M�jlighet att avsluta vid en dialog, var inte implementerat innan
- Menyalternativ f�r fix f�r autentiseringsbug av MAB
### Caveat
- Menyalternativ tre ger ingen feedback n�r det fungerar, och det tar en stund

## 1.9.2
### Changed
- Optimerat kod
- C9k saknade en trap f�r smart-license
- Funktion f�r paus efter ett range-kommando
- Optimerat CleanFlash f�r att anv�nda funktionen FindImage
### Caveat
- Sista versionen med st�d f�r VBScript

## 1.9.1
### Fixed
- R�ttat ordning n�r externa kodblock laddas
- Verifiering att det �r en seriell session och inte ssh
- Problem med C9k som numera anv�nder ny metod f�r uppgradering. Gjort om hela funktionen UpgradeCheck
	
## 1.9.0
### Added
- Flyttar ut kodblock gemensamma i externa filer som laddas efter behov. F�renklar uppdateringen av kod mellan scripten
- Verifierar all inmatning s� att det �r r�tt formaterat. Skall hindra krasch n�r felaktigt v�rde matas in

## 1.8.2
### Fixed
- Optimerat Do�Loop
- Fixat fel i mode detektering som ibland inte fungerade om text skrevs till console av switchen
- Konsekvent anv�ndande av network(0)

## 1.8.1
### Fixed
- R�ttat ett fel r�rande med C9300-NM-8X
- Automatiserat dialogen runt C9300-NM-8X
 
## 1.8.0
### Added
- Ny models-fil med ny image f�r C9K
- Ny switch C9300-24S som enbart inneh�ller trunkportar
- Automatiserat uppt�ckt av befintliga vlan och management vlan i script f�r enstaka portar
- Detektering av 8x10Gb modul i C9300
- Om secretfile �r inaktuell, �ppnas ett nytt f�nster d�r du kan ladda ned ny
- Detektering av exec, priv exec och config mode
### Changed
- �ndrat hantering av skapandet av trunkportar. Bytt fr�n subrutin till funktion
- �ndrat skapandet av ise-portar. Bytt fr�n subrutin till funktion
- Via ISE Accessport kan nu �ven klassiska trunkportar bli accessport med ISE
### Fixed
- R�ttat dialogtext
- Rensat rester av uppdatering av C9K-modeller
- Fix f�r kvarl�mnad konf f�r default-gateway eller route efter uppgradering har utf�rts
 
## 1.7.3
### Added
- N�tverks variablerna lagras nu i en separat fil s� att man slipper editera koden inuti scriptet om detta skulle �ndras. Introducerar d�rmed filen networks.csv p� gemensam filyta.
- Scripten f�r enstaka portar har nu f�tt st�d f�r att k�ras p� vilken port som helst i switchen.
- Tagit bort sidbrytning som kom med C9k i vissa funktioner
### Changed
- G�r tillbaka till klassisk uppgradering p� C9K
- �ndrat FreeMem till en function
- �ndrat ordning f�r aes kryptering f�r typ 0 l�senord �r p� v�g bort i c9k
 
## 1.7.2
### Added
- Lagt till st�d f�r L3-tj�nsten i KBN
- St�d f�r dhcp snooping
- St�d f�r IBNS 2.0 som �r valbart p� utvalda switchmodeller
- Lagt in en ACL f�r VTY access, som �r best-practise
### Changed
- �ndrat paus i SendLine till 175ms
### Fixed
- R�ttat fel i CleanFlash-modulen f�r 2960X

 
## 1.7.1
### Added
- Lagt till funktion f�r flow-control som g�r att man slipper specialinst�llningar i sessionen
### Changed
- Ytterligare st�dat dialoger
- B�ttre felhantering
### Fixed
- Problem med uppgraderingsmodulen. Skrivit om mycket kod f�r att hantera en egenhet som g�r att ftp ibland inte fungerar.
- Gl�mt aktivera CleanFlash i version ## 1.7.0
- Tv� fel i global f�r 2960 med 15.0
 
## 1.7.0
### Added
- Verifierat uppgradering av C9K
### Changed
- St�dat koden som hade blivit sv�r att h�lla uppdaterad
- Likriktat konfig runt popup rutor samt st�dat antal och standardval
- St�dat variabler
### Fixed
- Fixat ett fel som reserverade ip vid uppgradering
- Fixat verifiering av korrekt vlan
- Uppgradering felar ibland. Lade in 15sek f�rdr�jning innan ftp-�verf�ring
 
## 1.6.3
### Added
- Integration av Solarwinds f�r att hitta n�sta lediga ip och markera den Reserved
 
## 1.6.2
### Added
- Verifiering av switchnamn och ip mot ISE ifall de redan finns
 
## 1.6.1
### Added
- Lagt till modul f�r ISE REST API som l�gger till switchen som en ny network device
- Kontroll av version p� secrets.dat
### Changed
- �ndrat ordning f�r factory default. Fick alltid upp en fr�ga om att spara konfig

## 1.6.0
### Added
- Introducerar fil f�r switchmodeller och dess unika inst�llningar
- Introducerar fil f�r nycklar, token och l�senord
- Fixat fel i uppdateringsmodulen som gjorde att felaktig konfiguration sparades vid omstart
- St�dat variabler som anv�nds
- Lagt till modul som kontrollerar ledigt utrymme p� flash
- Lagt till modul som kan rensa gamla .bin-filer
- Mer och b�ttre dokumentation i koden
- Konsoliderat bitar av switchkonfiguration
