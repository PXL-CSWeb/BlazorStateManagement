# Blazor State Management

## Documentatie
https://learn.microsoft.com/en-us/aspnet/core/blazor/state-management?view=aspnetcore-8.0&pivots=server

## Setup
In dit voorbeeld gebruiken we de Blazor template voor .NET8:
- Maak een nieuwe *Blazor Web App* project
![blazor](assets/project_blazor.png)
- Project name: **BlazorStateManagement**
![blazor](assets/project_configure.png)
- Selecteer *.NET8.0* als framework en *Server* als render mode
![blazor](assets/project_server.png)

## Probleem
Wanneer we de applicatie starten en naar de Counter-page navigeren kunnen we de counter variabele telkens met één verhogen.
De waarde van de variabele wordt echter gereset wanneer we de pagina opnieuw laden. De oorzaak hiervan is dat de *state* van de applicatie niet bewaard wordt.
![blazor](assets/counter_refresh.gif)

## Oplossing
Een mogelijke oplossing is om alle data te bewaren in een (al dan niet relationele) database zoals SQL Server. Dit is helaas niet altijd mogelijk maar net zoals in dit geval vooral vaak overkill.
In dit geval is het dus beter de waarde van deze variabele te bewaren in de *localStorage* van de browser. De localStorage kan worden benaderd door gebruik te maken van [JavaScript interoperability](https://learn.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/?view=aspnetcore-8.0), hiermee kan JavaScript worden aangeroepen vanuit Blazor C#.
Omdat deze functionaliteit vaak nodig is, is er een NuGet package beschikbaar die dit voor ons afhandelt: [Blazored.LocalStorage](https://github.com/Blazored/LocalStorage)

## Oefening
1. Installeer de Blazored.LocalStorage package			
![localStorage](assets/nuget_localstorage.png)		
De [Blazored](https://github.com/Blazored/) collectie bevat nog enkele andere leuke packages die je kan gebruiken in je Blazor projecten!
2. Registreer de service in de *Program.cs* file

        builder.Services.AddBlazoredLocalStorage();

3. Lees de documentatie van de [Blazored.LocalStorage](https://github.com/Blazored/LocalStorage?tab=readme-ov-file#usage-blazor-server) en los bovenstaand probleem op door de waarde van de counter variabele te bewaren in de *localStorage*. Uiteraard dient de waarde ook opnieuw uitgelezen te worden wanneer een component gerenderd wordt.