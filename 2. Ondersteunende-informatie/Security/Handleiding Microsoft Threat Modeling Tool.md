---
title: Handleiding Microsoft Threat Modeling Tool
---
# **Stap 1. Downloaden**
Om toegang te krijgen tot de Microsoft Threat Modeling Tool, kun je de onderstaande link openen. Scroll vervolgens helemaal naar beneden op de pagina en onder het kopje "Next Steps" vind je de downloadlink voor de tool. Klik erop om de tool te downloaden.

[Microsoft Threat Modeling Tool downloaden](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool)
# **Stap 2. Nieuwe model aanmaken**
Voordat je een [threat model](1.%20Wat%20is%20een%20Threat%20Model.md) kan maken moet er eerst een nieuw project worden opgestart.
![[stap2.png]]

## **Stap 3. Ontwerp een thread model**
Aan de rechterzijde van het scherm bevinden zich de beschikbare componenten waarmee het thread model kan worden opgebouwd. In de onderstaande afbeelding zijn de volgende componenten gebruikt: 
- Generic Data Flow (verzoek en respons) om de stroom van verzoeken te illustreren. 
- Generic TrustLine Boundary om de locaties van de niet-vertrouwde grenzen aan te geven. 
- Browser 
- Webapplicatie 
- Web-API 
- Database 

**Een handige tip**: door op een component te klikken, kunt u aan de rechterzijde van het scherm, onder het gedeelte van het component, de naam wijzigen.
![[sources/security/microsoft_threat_modeling_tool/stap3.png]]

# **Stap 4. Rapport generen**
Om een volledig rapport te genereren, klik je bovenaan op "Rapports". Selecteer vervolgens de optie "Generate full rapport". Zodra je een naam hebt ingevoerd, wordt het rapport automatisch gegenereerd. In dit rapport worden alle mogelijke kwetsbaarheden op basis van het **STRIDE-model** beschreven, samen met mogelijke maatregelen om ze te verminderen.
![[stap4.png]]

# Stap 5. Threat List genereren
Om de Threat List te genereren die je kunt exporteren naar csv klik je bovenaan op Analysis View.

![[stap5_1.png]]

Klik vervolgens op ‘Export to csv’.

![[stap5_2.png]]

Importeer het .csv bestand in Excel:

![[stap5_3.png]]
