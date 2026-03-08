# GoalPay API - Exemple d'intégration Next.js

Acceptez les paiements Mobile Money en quelques minutes avec GoalPay.

Ce dépôt montre comment intégrer l'API de paiement GoalPay dans une
application Next.js, incluant la création d'un checkout, la redirection
vers la page de paiement et la gestion des webhooks.

GoalPay est une plateforme de paiement et portefeuille numérique conçue
pour Madagascar. Elle permet aux entreprises et aux développeurs
d'accepter facilement les paiements en ligne via Mobile Money ou via un
compte GoalPay.

------------------------------------------------------------------------

# 🚀 Fonctionnalités de GoalPay

GoalPay fournit une infrastructure de paiement complète pour les
entreprises et développeurs.

## Pour les développeurs

-   API REST simple
-   Authentification par token
-   Création rapide de checkout
-   Support des webhooks pour les événements de paiement (en production et test local)
-   Dashboard marchand avec statistiques

## Pour les marchands

-   Acceptation des paiements via comptes GoalPay
-   Dépôts et retraits via Mobile Money
-   Notifications de paiement en temps réel
-   Statistiques détaillées des ventes
-   Transactions sécurisées

## Pour les utilisateurs

-   Dépôt et retrait via Mobile Money
-   Transfert d'argent entre utilisateurs
-   Paiement en ligne instantané
-   Historique des transactions

------------------------------------------------------------------------

# 🧠 Comment fonctionne GoalPay

1.  Le serveur marchand crée un checkout via l'API GoalPay
2.  L'API retourne une URL de paiement
3.  L'utilisateur est redirigé vers la page de paiement GoalPay
4.  L'utilisateur effectue le paiement
5.  GoalPay envoie un webhook au serveur marchand
6.  Le système marchand met à jour la commande

Flux simplifié :

Client → Serveur Marchand → API GoalPay → Page de paiement\
↓\
Webhook

------------------------------------------------------------------------

# ⚡ Démarrage rapide

Cloner le projet :

`git clone https://github.com/Goal-Company/goalpay-nextjs-demo`

Entrer dans le dossier :

`cd goalpay-nextjs-example`

Installer les dépendances :

`npm install`

Lancer le projet :

`npm run dev`

------------------------------------------------------------------------

# 💾 Migration de la base de données

Génération base de données :

`npx drizzle-kit generate`

Migration :

`npx drizzle-kit migrate`

------------------------------------------------------------------------

# 🔑 Variables d'environnement

Créer un fichier `.env` à partir du copie du `.env.example` 

GOALPAY_ACCESS_KEY=votre_token_api 

GOALPAY_WEBHOOK_SECRET=votre_webhook_key

PAYMENT_GOALPAY_URL=[https://api.goalpay.pro](https://api.goalpay.pro/api/payement/service)  

------------------------------------------------------------------------

# 💳 Créer un paiement (exemple)

Exemple avec JavaScript :

``` javascript
const response = await fetch("[https://api.goalpay.pro/checkout](https://api.goalpay.pro/api/payement/service)", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
  "description": "Panier num 20200320",
  "access": "TGP_RSIGJQXYTSCXS6NX",// votre token
  "reference": "ref000111001110101",// une référence unique dans votre système 
  "amount": 100000,
  "currency": "Ar",
  "metadata": [
    {
      "label": "Conception logo",
      "unit_price": 100000,
      "quantity": 1
    }
  ]
})
})

const data = await response.json()
console.log(data.checkout_url)
```

Redirigez ensuite l'utilisateur vers `checkout_url` pour finaliser le
paiement.

------------------------------------------------------------------------

# 📚 Documentation

Documentation complète :

https://goalpay.pro/docs

------------------------------------------------------------------------

# 🔐 Bonnes pratiques de sécurité

Ne jamais exposer le token API côté frontend.

Toujours :

-   créer les paiements côté serveur
-   vérifier les webhooks
-   enregistrer les ID de transaction (order reférence de goalpay et votre reference)
-   journaliser les événements de paiement

------------------------------------------------------------------------

# 🤝 Contribution

Les contributions sont les bienvenues.

Vous pouvez proposer des améliorations via une Pull Request.

------------------------------------------------------------------------

# 🇲🇬 À propos de GoalPay

GoalPay est une plateforme de paiement malgache conçue pour simplifier
les transactions en ligne pour les entreprises et particuliers à
Madagascar.

Elle permet d'accepter des paiements en ligne, d'intégrer le Mobile
Money et d'automatiser les transactions via une API simple pour les
développeurs.

------------------------------------------------------------------------

# 📬 Support

Email : goalpay.mg@gmail.com

Documentation : https://goalpay.pro/docs 

Donation : https://donation.goalpay.pro 

