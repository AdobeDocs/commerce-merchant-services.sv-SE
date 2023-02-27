---
title: Allmän konfiguration
description: Konfigurera allmänna inställningar för att aktivera [!DNL Store Fulfillment] för er butik. Konfigurera globala tilläggsinställningar, systeminställningar för loggning, datasynkronisering och säkerhet. Tillhandahåll nyckeldata för att möjliggöra integrering mellan Adobe Commerce och Store Fulfillment services.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 0%

---

# Konfiguration av butikstjänst och försäljning

Konfigurera [!DNL Store Fulfillment] från [!DNL Commerce] Administratören kan aktivera tillägget, ange tilläggsinställningar, konfigurera säkerhetsinställningar för Store Assist-appanvändare och ange alternativ för leveransmetoder.

>[!IMPORTANT]
>
>Konfigurationen av tjänsten Store Fulfillment gäller endast efter att du har anslutit Adobe Commerce-instansen och [!DNL Store Fulfillment] app. Se [Connect Store Fulfillment](connect-set-up-service.md).

## Hantera inställningar för uppfyllandetjänster för butik

Hantera inställningar för Butiksuppfyllelse-tjänster från [!DNL Commerce Admin Store Configuration] -menyn.

- Aktivera tillägget, konfigurera globala inställningar och ange säkerhetsalternativ för användaranslutningar och konton för appen Store Assist genom att välja **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

   ![Konfiguration av Admin Store-tjänster för Butiksuppfyllelse](assets/store-services-admin-sf-config.png)

- Konfigurera leveransmetoder genom att välja **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

   ![Admin Store-försäljningskonfiguration för Store-uppfyllelse](assets/store-sales-admin-sf-deliver-config.png)

## Grundinställningar

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>Det pris du debiterar kunden för upphämtning i butik. Standardvärdet är noll.</td>
<td>Webbplats</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>Radien, i kilometer, som ska användas när en kund söker efter en butiksupphämtningsplats i butikens utcheckning. Sökresultaten returnerar endast butiker som finns inom den angivna sökradien.</td>
<td>Webbplats</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>Meddelande som visas när en kund väljer butiksupphämtning för ett objekt som inte är tillgängligt för butiksupphämtning. Du kan anpassa standardtexten om det behövs.
</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>The [!UICONTROL Search Radius] inställningen används bara om du har konfigurerat [lagringsplats och mappningsinställningar](store-location-map-provider-setup.md) för Adobe Commerce.

## Aktivera lösningen för att uppfylla kraven i Store

Aktivera [!DNL Store Fulfillment] för att lägga till de funktioner som finns i butik och krångel till shoppings- och utcheckningsupplevelserna i din Adobe Commerce-butik.

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Aktivera eller inaktivera lösningen. När det här alternativet är aktiverat konfigureras och används funktionen för att uppfylla kraven i Store och anslutningen mellan din Adobe Commerce-butik och [!DNL Store Fulfillment] tjänster. När funktionen är inaktiverad inaktiveras alla funktioner för Store Fulfillment och det finns ingen kommunikation mellan Adobe Commerce och Store Fulfillment-tjänster. Orderinformationen kan inte behandlas eller tas emot.</td>
<td>Webbplats</td>
<td>Ja</td>
</tr>
</tbody>
</table>

## Lägg till kontoautentiseringsuppgifter

<table>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Välj antingen <i>[!UICONTROL Sandbox]</i> eller <i>[!UICONTROL Production]</i><br></br>Markera [!UICONTROL Sandbox] möjliggör kommunikation med sluttjänster i en testmiljö.<br></br>Markera [!UICONTROL Production] möjliggör kommunikation med sluttjänster i en levande miljö.<br></br>Du får en uppsättning autentiseringsuppgifter för varje miljö och kan hantera båda uppsättningarna i samma installation. <br></br>Spara inloggningsuppgifterna innan du validerar anslutningen.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>URL:en till Walmart Store Fulfillment API-slutpunkten. Detta måste vara den fullständiga URL som anges under introduktionsprocessen. Butikskunder som uppfyller kraven får både en sandbox- och en Production URL. När du lägger till värdena måste du kopiera och klistra in den fullständiga URL:en, inklusive avslutande snedstreck "/".</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>URL:en till Walmart Store-slutpunkten för autentisering av uppfyllelse. Värdet måste vara den fullständiga URL som anges under introduktionsprocessen. Du får både en sandbox- och en Production URL. När du lägger till värdena måste du kopiera och klistra in den fullständiga URL:en, inklusive avslutande snedstreck "/".</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Ditt unika handlar-ID (tenant) som tillhandahålls under introduktionsprocessen. Detta ID används för att dirigera beställningar för att säkerställa att dina handlarbutiker tar emot dem.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>Det unika integrerings-ID som angavs under introduktionsprocessen. Detta ID används för att autentisera all kommunikation mellan Adobe Commerce och butikssluttjänster</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>Den unika integreringsnyckeln som tillhandahålls under introduktionsprocessen. Den här nyckeln används för att autentisera all kommunikation mellan Adobe Commerce och butikssluttjänsten.</td>
<td>Global</td>
<td>Ja</td>
</tr>
</table>

När du har konfigurerat [!UICONTROL Account Credentials], markera <strong>[!UICONTROL Validate Credentials]</strong> för att verifiera och upprätta en anslutning till butikssluttjänsten för första gången.

## Konfigurera loggning

Loggar för butiksleveranser är tillgängliga i loggfilen `var/log/walmart-bopis.log`.

Be systemadministratören att konfigurera dina miljöer så att de tillåter undantagshantering så att API-relaterade undantag kan fångas in via brandväggen eller cachen.

Eftersom programloggfilen kan växa snabbt, bör du bara aktivera loggning för programmet en kort tid vid behov, t.ex. vid felsökning av problem med att lagra för en [!DNL Commerce] beställa. Den här konfigurationen förhindrar problem med svarstid i produktionsmiljöer som orsakas av stora loggfiler.

>[!TIP]
>
>För Adobe Commerce lokala installationer ber du systemadministratören att ställa in loggrotation för `var/log/walmart-bopis.log` för att minimera storleken. För Adobe Commerce lokala installationer, se [Loggrotation](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) i _Installationshandbok för Adobe Commerce_. Information om projekt för molninfrastruktur för Adobe Commerce finns på [Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>Felsökningsläge används för att öka den loggade aktiviteten i integreringen. När det är inaktiverat loggas ingen felsökningsinformation. När det här alternativet är aktiverat loggas all felsökningsinformation <br></br>Alla loggade data finns i filen: <pre>var/log/walmart-bopis.log</pre>
<td>Global</td>
<td>Nej</td>
</tr>
</tbody>
</table>

## Hantera ordersynkronisering

Konfigurera inställningarna för att hantera felhantering för ordersynkronisering, katalogattribut som ska användas för streckkodsskanning vid orderplockning och konfigurera orderbatchstorlekar för butikens leveranskö.

Du kan visa information om ordersynkroniseringsåtgärder från kontrollpanelen för hantering av uppfyllandekö i Store i Admin (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### Felhantering för synkronisering

<table>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Anger nya försök att utföra en postsynkroniseringsåtgärd efter att ett kritiskt fel har inträffat.<br></br>Kritiska fel inträffar när integreringen inte lyckas få ett positivt svar från sluttjänsten. Detta kan inträffa när tjänsten är nere eller när det finns ett fel i den orderdata som skickas.<br></br>När tröskelvärdet för nya försök nås, finns objektet kvar i en kö men bearbetas inte igen. Visa alla objekt med fel från <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> Hantering i administratören. Om du vill felsöka objekt som misslyckas regelbundet kontaktar du kontohanteraren.</td>
<td>Global</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Aktivera felmeddelanden för att få ett e-postmeddelande när [!UICONTROL Retry Critical Error Threshold] nås för en order. Meddelandet innehåller all tillgänglig information om felet.</td>
<td>Global</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>En kommaavgränsad lista över mottagarnas e-postadresser för felmeddelanden.</td>
<td>Global</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>Anger den e-postmall som används för att meddela mottagare om ordersynkroniseringsfel. En standardmall anges. Det stöder inte anpassning.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
</table>

### Ordersynkronisering

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>Katalogattributet som lagrar den inläsbara koden för motsvarande objekt på handelsplatserna.<br></br>Om du bara har en befintlig handelsplats är det troligt att du använder UPC-koder, medan e-handelskanalen identifierar produkter efter SKU. Om detta är ditt scenario väljer du det katalogattribut som innehåller UPC-koden.<br></br>Den här inställningen säkerställer att beställningar som skickas till dina butiker listar artiklar med rätt identifierare så att butikskollegierna kan söka igenom artiklar korrekt under plockningsprocessen.<br></br>Om du är osäker kan du kontrollera med de som är knutna till tjänsten Leverans och plockning för att avgöra vilket attribut som ska skickas. Du kan behöva lägga till rätt attribut till Adobe Commerce produktattributuppsättning om attributet inte finns med i databasen.</td>
<td>Webbplats</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>Katalogattributet som lagrar streckkodskällan för motsvarande objekt på handelsplatserna.<br></br>Den här inställningen säkerställer att beställningar som skickas till dina butiker listar artiklar med rätt identifierare så att butikskollegierna kan skanna artiklar korrekt under plockningsprocessen. Du kan välja mellan följande alternativ: SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR och Price Embedded UPC.<br></br>Om du är osäker väljer du det alternativ som mest liknar värdena i [!UICONTROL Barcode Source] -attribut. Butikskollegister kan fortfarande matcha artiklar manuellt från sin plocklista.</td>
<td>Webbplats</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>Det högsta antalet objekt som kan skickas från butikens leveranskö samtidigt.<br></br>BOPIS-beställningar skickas till tjänsten i grupp med regelbundna mellanrum. Med den här inställningen kan du styra gruppstorleken.<br></br>Standardvärdet är 100 objekt. Beroende på ordervolym och kapacitet kan du behöva justera det här värdet uppåt eller nedåt.</td>
<td>Global</td>
<td>Nej</td>
</tr>
</tbody>
</table>

## Aktivera leveransalternativ för uppfyllande av leveransvillkor

Konfigurera alternativ för leverans av fullgörande i Store som avgör vilka alternativ för hämtning i butiken och leverans i hemmet som är tillgängliga för dina Adobe Commerce-butiker.

### Leverera till butik

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>Inställningen för leverans till butik baseras på dina befintliga funktioner för leverans till butik. Om du använder Inventory management, eller om du kan acceptera och utföra order på handelsplatser utan lager via lageröverföring från butik till butik, ställer du in det här alternativet på "Ja".<br></br>Om du inte kan stödja alternativet för leverans till butik eller inte vill erbjuda det, ställer du in på "Nej". När det är inaktiverat finns artiklar i din katalog med noll lager för en handlarbutik, eller artiklar som ligger under den platsens [!DNL Out of Stock Threshold], erbjuds inte med alternativ för hämtning i butiken.<br></br>Det här är en global inställning som kan justeras per handelsplats.</td>
<td>Global</td>
<td>Nej</td>
</tr>
</tbody>
</table>

### Leverera från butik

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Aktiverar eller inaktiverar alternativet Home Delivery i dina butiker. När det här alternativet är aktiverat räknas din butiksplats som en samling med andra tilldelade källor i det lager som är kopplat till din webbplats.<br></br>Med Inventory management standardtjänster [!DNL Ship from Store] är ett inbyggt alternativ som inte kan inaktiveras. Med Store Fulfillment-lösningen kan du aktivera eller inaktivera den.<br></br>Detta är en global inställning. Du kan även justera den här inställningen per handelsplats och produkt.</td>
<td>Global</td>
<td>Nej</td>
</tr>
</tbody>
</table>


## Hantera konton och behörigheter för användning av appar för Store

Konfigurera inställningarna för användarkontot och lösenordssäkerheten för Store Fulfillment App samt tvåfaktorsautentisering.

### Appsäkerhet

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>Tidsramen, i sekunder, för att en butiksassocierad användarsession ska förbli aktiv före automatisk utloggning. Giltiga värden är från 60 till 31536000.</td>
<td>Global</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>Anger antalet misslyckade inloggningsförsök som tillåts innan en butikskoppling låses ut från sitt konto.<br></br>Om du vill inaktivera kontoutelåsning anger du värdet 0.</td>
<td>Global</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>Antal minuter som ett konto ska låsas efter ett inloggningsfel.</td>
<td>Global</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>: Kräv att användaren ändrar sitt lösenord efter kontoinställningarna.<br></br><em>[!UICONTROL No]</em>: Rekommenderar användaren att ändra lösenord efter kontoinställning.</td>
<td>Global</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>Antalet dagar som ett lösenord förblir giltigt innan ett obligatoriskt lösenord ändras. Lämna tomt om du vill inaktivera det här alternativet.</td>
<td>Global</td>
<td>Nej</td>
</tr>
</tbody>
</table>

## Leveransmetoder

Butiksuppfyllelse fungerar genom att utöka Adobe Commerce [!DNL In-Store Delivery] funktioner. När du har installerat tillägget kan du konfigurera leveransmetoder i butiken med följande utökade inställningar som läggs till i Admin.

- **Plocka upp i butik**—Erbjud alternativ för leverans i butik under utcheckningsprocessen Detta är det vanligaste leveransscenariot för BOPIS-order.

- **[!UICONTROL Curbside pick up]**-Erbjud kunderna möjlighet att parkera på en butik och få sina beställningar levererade till dem av en butikspartner.

Konfigurera de här inställningarna från administratören genom att välja <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>Mer information om hur du konfigurerar leveransalternativ för butiker finns i [Butiksleverans](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) i _Adobe Commerce Användarhandbok_.


### Konfiguration av leveransmetoder

Med leveransmetoden i butik kan kunden välja en källa som ska användas som hämtningsplats under utcheckningen.

<table>
<thead>
<tr>
<td><strong>Fält</strong></td>
<td><strong>Beskrivning</strong></td>
<td><strong>Omfång</strong></td>
<td><strong>Obligatoriskt</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>Aktivera eller inaktivera det alternativ för hämtning i butik som är tillgängligt vid utcheckning för kunder som väljer butiksupphämtning. När hämtningen i butiken är inaktiverad visas inte alternativet.<br></br>Den här globala inställningen gäller alla butiksplatser. När det här alternativet är aktiverat kan du selektivt inaktivera det på butiksplatsen.</td>
<td>Webbplats</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>Aktivera eller inaktivera alternativet för hämtning vid utcheckning för kunder som väljer butiksupphämtning.<br></br>Den här globala inställningen gäller alla butiksplatser. När det här alternativet är aktiverat kan du selektivt inaktivera det på butiksplatsen.</td>
<td>Webbplats</td>
<td>Nej</td>
</tr>
</tbody>
</table>

### Rubrikkonfiguration för leveransmetod

<table>
<thead>
<tr>
<th><strong>Fält</strong></th>
<th><strong>Beskrivning</strong></th>
<th><strong>Omfång</strong></th>
<th><strong>Obligatoriskt</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Rubrik för hemleverans</strong></td>
<td>Anger den rubrik som ska visas för alternativet Home Delivery i områdena product, cart och checkout. Leverans i hemmet avser Adobe Commerce standardfunktioner för frakt - från ett lagerställe, av en fraktfirma eller direkt till den leveransadress kunden tillhandahåller. </br></br>Etiketten påverkar inte etiketterna för leveransmetoden för det valda transportföretaget.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Beskrivning av hemleverans</strong></td>
<td>En valfri beskrivning som visas när hemleveranstitel visas för kunderna. Beskrivningen är oftast ett statiskt meddelande som förmedlar dina löften. Några exempel:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Butikens plocktitel</strong></td>
<td>När en kund får leveransalternativ och butiksupphämtning är tillgänglig visas den här etiketten. </br></br>Du kan anpassa den här etiketten, som visas i områdena för produkt, kundvagn och utcheckning.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<td><strong>Beskrivning av butiksinhämtning</strong></td>
<td>Var än Butiksväljarens titel visas kan du inkludera en beskrivning. Det här statiska meddelandet hjälper till att förbättra kundkommunikationen i samband med upphämtning av butiker. Några exempel:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Plockningsrubrik i butik</strong></td>
<td>När Pickup i butik är aktiverat visas den här titeln för kunderna som leveransalternativ för Pickup i butik. Du kan anpassa dess etikett.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<tr>
<td><strong>Urbside Pickup Title</strong></td>
<td>När Blockside Pickup är aktiverat visas alternativet för kunderna som en typ av leveransalternativ för Butik Pickup. Du kan anpassa etiketten här.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Instruktioner för butiksinhämtning</strong></td>
<td>När en beställning är klar att hämtas i butikerna får kunden ett mejl. Om kunden valde [!DNL In-Store Pickup] under utcheckningen kan du anpassa hämtningsinstruktionerna här. </br></br>Det här är en global inställning som gäller alla butiksplatser. Du kan också anpassa instruktionerna på butiksplatsnivå.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Instruktioner för hämtning av badsidor</strong></td>
<td>Anger anpassade instruktioner för orderhämtning som ska inkluderas i kundens e-postmeddelanden för beställningar av snabbköp. </br></br>Det här är en global inställning som gäller alla butiksplatser. Du kan också anpassa instruktionerna på butiksplatsnivå.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Beräknad plockningstid för lead</strong></td>
<td>Antal minuter som krävs innan en order tas emot, har uppfyllts och är klar att hämtas. Den här informationen visas för kunden när denne väljer en butiksplats för leveransalternativet Butiksplockning. Detta är en global inställning som gäller alla butiksplatser. Du kan också anpassa ledtiden på butiksplatsnivå.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Etikett för beräknad hämtningstid</strong></td>
<td>Visar den beräknade tiden tills en order är tillgänglig för kundhämtning. Den här informationen visas för kunderna när de väljer en butiksplats för [!DNL In-Store Pickup] leveransalternativ. </br></br>När du anpassar den här etiketten kan du använda koden <code>%1</code> för att infoga <strong>Beräknad plockningstid för lead</strong>. Till exempel:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Det här är en global inställning som gäller alla butiksplatser. Du kan också anpassa ledtiden på butiksplatsnivå.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>Butiksvy</td>
<td>Nej</td>
<tr>
<td><strong>Ansvarsfriskrivning för hämtningstid</strong></td>
<td>Innehållet som visas på produktsidan i verktygstipset som visar butikstid, helgdagar, oväntade stängningar osv.</td>
<td>Butiksvy
</td>
<td>Nej
</td>
</tr>
</tbody></table>

### Konfiguration för Stock-tillgänglighetsrubriker

<table>
<thead>
<tr>
<th><strong>Fält</strong></th>
<th><strong>Beskrivning</strong></th>
<th><strong>Omfång</strong></th>
<th><strong>Obligatoriskt</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>I lager</strong></td>
<td>När en kund använder butikens positionerare visas lagertillgängligheten för de aktuella artiklarna för varje plats. </br></br>Du kan anpassa <em>[!UICONTROL in-stock]</em> statusetikett här.</br></br></td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Ej i lager</strong></td>
<td>När en kund använder butikens positionerare visas lagertillgänglighet för alla aktuella artiklar för varje plats.</td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
<tr>
<td><strong>Delvis i lager</strong></td>
<td>När en kund använder butikens positionerare, visas lagertillgänglighet för alla aktuella artiklar för varje plats. </br></br>Du kan anpassa <em>[!UICONTROL partially in-stock]</em> statusetikett här.</br></br></td>
<td>Butiksvy</td>
<td>Nej</td>
</tr>
</tbody></table>

