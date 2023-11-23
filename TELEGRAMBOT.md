# Prima parte: chat bot  
Telegram ha due tipi di bot: chat bot e inline bot. I chat bot usano i comandi (come `/start` , `/help` ) per
interagire tra utenti. Gli inline bot possono invece essere chiamati da qualsiasi parte e aiutano gli utenti a
trovare e inviare contenuti dal vostro bot a qualsiasi chat che desiderano. In questa sede ci occupiamo dei
chat bot.  
## Step 0.1: Scaricare Node.js e npm  
Qui ci sono i link alla versione di [Node.js](https://hackerstribe.com/tag/node-js/) che useremo per questo workshop:  
Windows: <https://nodejs.org/dist/v6.6.o/node--v6.6.o--x64msi> 
MacOS: <http://nodejs.org/dist/v6.6.o/node--v6.6.o.pkg>  
Linux: dovreste già sapere come procurarvi Node.js  
## Step 0.2: Telegram  
Prima di fare un [Bot Telegram](https://hackerstribe.com/tag/bot-telegram/), avrete bisogno di un **account Telegram**. Andate su [telegram.org/dl](https://desktop.telegram.org/) e  
create il vostro account.  
## Step 1: Creiamo la directory di progetto  
Ora che abbiamo Node.js e npm installati e il nostro account Telegram è pronto, possiamo partire col  
nostro lavoro. Aprite il vostro terminale preferito a digitate questi comandi:  

![image](https://github.com/Smrazzz/BotTelegram/assets/151780878/119d1ac0-9eac-4503-a5cd-6f878098591d)  

Adesso che abbiamo una directory per il nostro bot Telegram, abbiamo bisogno di un `package.json` , se  
non siete neofiti di Node.js, non è necessario che vi spieghi a cosa serve. Altrimenti sappiate che molto  
banalmente si può considerare come un descrittore del nostro progetto. Un file che indica nome,  
descrizione e fra le altre cose anche le dipendenze (intese come pacchetti software) necessari al nostro  
programma per funzionare.  
Per crearlo molto semplicemente, dalla directory del nostro progetto lanciamo il comando:  

![image](https://github.com/Smrazzz/BotTelegram/assets/151780878/52448ff6-68e3-40da-805f-569ee9ab8174)  
Questo dirà al client **npm** di inizializzare la nostra project directory con un `package.json` predefinito.  
Cliccate Invio a tutti i prompts, possiamo occuparci di “compilaro” più tardi.  
## Step 2: Installate i pacchetti necessari  
Per questo progetto, abbiamo bisogno soltanto di 1 pacchetto npm.  
Un pacchetto npm è sostanzialmente un pezzo di codice nel registro npm che possiamo scaricare con un  
semplice comando, ` npm install ` .  
Noi andremo ad usare un pacchetto chiamato `node-telegram-bot-api `e possiamo installarlo così:  

![image](https://github.com/Smrazzz/BotTelegram/assets/151780878/3e19fbc2-e954-4776-bb54-d74b613d9760)  
La parte `--save` indica a npm di salvare questo pacchetto nel nostro **package.json** cosicché sarà più  
facile installarlo dopo, senza ulteriori complicanze.  
## Step 3: creare il bot Telegram  
Su Telegram, contattate **@botfather** e usate il comando `/newbot` per creare un nuovo bot.  
Chiamatelo come preferite.  
## Step 4: scriviamo un po di codice!  
Adesso che abbiamo il nostro bot, possiamo usarlo per interfacciarci con Telegram e le sue API.  
Create un file index.js nella vostra project directory, poi apritelo nel vostro text editor preferito.  
Qui c’è qualche semplice codice “Hello world” che ho scritto per assistervi in questo step.  
 ```
var TelegramBot = require('node-telegram-bot-api'),
// Be sure to replace YOUR_BOT_TOKEN with your actual bot token on this line.
telegram = new TelegramBot("YOUR_BOT_TOKEN", { polling: true });
telegram.on("text", (message) => {
telegram.sendMessage(message.chat.id, "Hello world");
});
```
Sostanzialmente, ciò che questo codice fa è includere la libreria che abbiamo scaricato da npm  
precedentemente, poi istanziare un nuovo oggetto “bot Telegram” con il nostro token e dirgli di  
interrogare costantemente Telegram in cerca di eventuali nuovi messaggi.  
Poi lo ascolterà per l’evento “text” (che in questa libreria è un semplice messaggio di testo) e invierà un  
messaggio alla chat nella quale il messaggio originario era stato salvato dicendo “Hello world”.  
Ora, andate sul file index.js con questo comando:  
 ```
node index
```
Mandate un messaggio al vostro bot. Dovrebbe rispondere con “Hello World”. Se lo fa, ottimo! Altrimenti  
commentate sotto.  
## Step 5: Implementare un semplice comando  
Allo stato attuale, questo bot non è realmente utile.  
Rendiamolo utile aggiungendo un comando `/codeday` che ci dica quando finisce il CodeDay!  
Utilizzeremo due librerie in più qui, `codeday-clear` e `moment` .  
Codeday-clear è la libreria ufficiale Node.js per interagire con le API di Clear.  
Clear è il nostro sistema interno di gestione del CodeDay e ha un API molto semplice da usare. Lo  
useremo per sapere la data finale del CodeDay e poi useremo moment per convertirla in un formato più  
adatto.  
Per installare queste librerie:  
```
npm install --save codeday-clear moment
```
Nel nostro codice, abbiamo bisogno di includere queste due librerie e rappresentare un esempio “Clear”.  
Da quando il Clear API richiede un accesso per Clear e un paio di API token/secret, ho creato una semplice  
app con permessi limitati apposta per questo workshop.  








