#  Quizly – Application de quiz de culture générale  

"Quizly” est une application mobile Android développée en Kotlin avec Jetpack Compose.  
Elle permet à l’utilisateur de tester ses connaissances générales à travers un quiz dynamique alimenté par une API publique en ligne.  

Le joueur choisit une catégorie et un niveau de difficulté, répond à une série de 10 questions, puis découvre son score final.  
Les résultats sont enregistrés localement grâce à une base de données interne (Room), afin de pouvoir consulter son historique des scores même hors connexion.  

Ce projet illustre les principales compétences du cours :  
- création d’écrans en Compose  
- gestion d’appels réseau avec Retrofit  
- stockage local avec Room  
- architecture MVVM 
- gestion d’état réactif avec ViewModel et Flow  

## Fonctionnalités principales  

1️⃣ **Accueil / Menu : Sélection du quiz**  
➡️ L’utilisateur choisit la catégorie et la difficulté, puis lance le quiz.  

2️⃣ **Quiz : Requête API + interactions**  
➡️ Affiche les questions issues de l’API avec 4 propositions de réponse aléatoires.  

3️⃣ **Résultats : Historique (Base de données locale)**  
➡️ Affiche le score obtenu et la liste des précédents résultats sauvegardés localement.  


##  API utilisée  

**Nom :** [Open Trivia DB](https://opentdb.com/api_config.php)  
**Type :** API publique et gratuite (aucune clé requise)  

=> Les réponses sont mélangées côté application pour chaque question.  



##  Architecture technique  

Architecture : MVVM (Model – View – ViewModel)

![Architecture MVVM du projet](images/architecture.png)



##  Description des couches  

### 🟢 Activity / UI Layer  
- Écrans composés en Jetpack Compose
- Observe les états exposés par le ViewModel via `collectAsState()`  

### 🔵 ViewModel Layer  
- Gère la logique du jeu et les états *(Loading, Success, Error)*  
- Appelle le Repository pour charger les questions ou sauvegarder le score  
- Utilise `viewModelScope.launch { }` et StateFlow

### 🟠 Repository Layer  
- Intermédiaire entre la logique et les sources de données  
- Combine les données de Retrofit (API) et Room (local)  

### 🟣 Data Layer  
- Retrofit → récupère les questions en JSON  
- Room → stocke les scores sous forme d’entités locales  



##  Technologies et dépendances  

- **Langage :** Kotlin  
- **UI :** Jetpack Compose  
- **Architecture :** MVVM  
- **Réseau :** Retrofit + Coroutines  
- **Stockage local :** Room  
- **Gestion d’état :** StateFlow + ViewModel  
- **Outils Android :** Navigation Compose, ViewModel, LiveData  


