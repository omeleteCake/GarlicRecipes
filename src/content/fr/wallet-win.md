# Table des Matières
- [Configuration du réseau](#configuration-du-réseau)
- [Créer un Portefeuille](#créer-un-portefeuille)
- [Diagnostic des anomalies](#diagnostic-des-anomalies)

# Configuration du réseau
La configuration du réseau est facile et rapide. Ça va vous permettre de connecter ton ordinateur au Réseau Garlicoin.

## Étape 1. Télécharger les fichiers
D'abord, vous devez télécharger les binaires de Windows [içi](https://garlicoin.io/downloads) aussi bien que [Fichiers de Démarrage Rapide](ROOT/files/wallet-win.zip).
Quand cela est fini, ouvrez les 2 fichiers (`.tar.gz` ET `.zip`), ensuite extrayez leur contenu dans un dossier (Dans ce tutuoriel, nous allons utiliser `C:\Garlic\`).  
![Garlic Folder With Files](https://i.imgur.com/YYqtODB.png)

## Step 2. Connexion au Réseau
Cela peut être fait de 2 façon, à travers l'interface visuelle (Recommandé) ou la ligne de commandes.  

### Interface visuelle
Dans le dossier, il devrait avoir un fichier nommé `Run-Network.bat`.  
Ouvrez le fichier; une fenêtre d'Invite de Commande devrait s'ouvrir. Vous devez vous assurez que vous autorisez l'accès au travers le pare-feu (si ça te le demande).  
<br>

Le program va rien dire, laisse le fonctionner en arriêre-plan. **Ne le ferme pas.**  
*Vous devrez l'ouvrir chaque fois que vous voulez utiliser votre Portefeuille (ou pendant le Minager Solo).*

### Ligne de commandes
Pour ceux qui ont plus d'expérience, ouvrez l'Invite de Commandes.  
Navigue à votre dosser Garlic en utilisant `cd`.  
Ensuite, exécutéz la commande : `garlicoind`.   
Windows peut te demander l'accès du Pare-feu, permettez-le.  
<br>

Le program va rien dire, laisse le fonctionner en arriêre-plan. **Ne le ferme pas.**  
*Vous devrez l'ouvrir chaque fois que vous voulez utiliser votre Portefeuille (ou pendant le Minager Solo).*


## Étape 3. Déplacement du fichier .conf vers Roaming\Garlicoin
Retour à ton dossier Garlic, il devrait y avoir un fichier appelé `garlicoin.conf`. Ce fichier doit être déplacé vers le dossier `Garlicoin` qui se trouve dans `AppData\Roaming`.  
<br>

Pour accéder à ce dossier, Ouvrez **RUN** (Windows + R), et tapez  `%appdata%`. Cela devrait ouvrir un dossier, localisez le dossier `Garlicoin` et déplacez le fichier `garlicoin.conf` vers celui-ci.

## Étape 4. Redémarrer le Réseau
Juste pour être certain que tout a été bien fait. Fermez votre fenêtre de Réseau (celui `Run-Network.bat`) en maintenant **Ctrl + C**.  
Maintenant, répetez **Étape 2**, tout devrait être pret.  
<br>

## Étape 5. Télécharger la chaîne à blocs (Blockchain)
Pendant que votre fenêtre du réseau est ouverte, ouvrez une nouvelle Invite de Commandes.  
Navigue vers ton dossier Garlicoin (utilise `cd C:\Garlic\`), et tapez `garlicoin-cli getblockchaininfo`.  
Cette commande affiche l'information sur la chaine à blocs que vous avez téléchargé, la valeur des `blocks` qui se trouve en haut est le nombre de blocs reçus. Vous pouvez exécuter cette commande plusieurs fois pour vérifier l'état. Dès qu'il arrive à la valeur  (https://explorer.grlc-bakery.fun/api/getblockcount)[ici] la synchronisation de votre chaine à blocs est finite.

# Créer un Portefeuille
Maintenant que vous avez le Réseau qui fonctionne, vous devez faire une adresse de Portefeuille.  

## Étape 1. Utiliser l'Invite de Commandes
Ouvrez **l'Invite de Commandes**. Vous devez localiser votre dossiez d'installation; vous pouvez le faire de cette façon:  
Si vous l'avez installé un lecteur différent, vous devez écrire la lettre de votre lecteur suivie par un deux-points. Par exemple, lecteur F serait `F:`. Ensuite, appuyez Entrée.   
Tapez `cd C:\Garlic\` (ou quel que soit votre dossier d'installation) et appuyez Entrée. 

## Étape 2. Faire une Nouvelle Adresse
Dans l'Invite de Commandes, écrivez cette commande: `garlicoin-cli getnewaddress`.  
Vous verrez une longue chaîne de lettres et de chiffres. Ceci est votre adresse Garlicoin. Assurez-vous de la copier et de la conserver quelque part.  
(Pour copier de l'Invite de Commandes, selectionnez l'adresse avec votre souris et ensuite, faites un clic-droit).  

*Quand quelqu'un veut te payer, vous l'envoyez cette adresse*

![Image of GetNewAddress](https://i.imgur.com/pjSUslM.png)

## Step 3. Getting Wallet Info
To make sure that you have done everything right (or to view your balance), you can type: `garlicoin-cli getwalletinfo` in that same Command Prompt.  
This should give you information about your balance, wallet, when your last transaction was...  
<br>

## Step 4. Backing Up the Wallet
Sometimes, the wallet app can fail and corrupt the wallet. If you wish to back it up before that happens (in order to recover it in case it does break), follow these steps:  
In a Command Prompt window (while the network is running), type the command: `garlicoin-cli backupwallet <path>`.  
This will save a `wallet.dat` file in at the given path. If your wallet ever gets corrupted, navigate to this folder:
- Windows: `%APPDATA%\Bitcoin`
- Linux: `~/.bitcoin/`
- MacOS: `~/Library/Application Support/Bitcoin/`

and overwrite the `wallet.dat` file inside the folder by the backup one.

## Step 5. Sending to Someone Else
If you ever wish to send Garlicoin to someone. You can use this command `garlicoin-cli sendtoaddress <bitcoinaddress> <amount>`.

That's it! You are done!

# Diagnostic des anomalies

## json\_rpc\_call failed, retry after 10 seconds
If you are getting this error, let it keep retrying. It should correct itself soon.

## garlicoind is not recognized
If you are getting this eror, it means that your Command Prompt is not opened in your installation directory. 
Make sure that you have used `cd C:\Path\To\Garlic\Folder` before running your command.

## garlicoin-cli is not recognized
If you are getting this eror, it means that your Command Prompt is not opened in your installation directory. 
Make sure that you have used `cd C:\Path\To\Garlic\Folder` before running your command.

## 0 blocks
Try changing your `.conf` file to have the content found on the [Changes page](./changes.html).

## HELP!
If the above troubleshooting steps do not work. You can ask in the Discord chat `#troubleshooting` or `#windows-mining` or contact me `@Pandawan#4158`.
