# Projet Réseau Aquarium

Ce projet simule un aquarium réseau avec un serveur qui gère les poissons et un client qui affiche leur position.

## Structure du projet

- **serveur/** : Contient le code source du serveur.
- **client/** : Contient le code source du client.
- **diag/** : Contient des diagrammes d'architecture.
- **poisson/** : Contient des ressources graphiques pour les poissons.

---

## Compilation et exécution

### Prérequis

- **Serveur** :
  - GCC (compilateur C)
  - Make

- **Client** :
  - Java 11 ou supérieur
  - Maven

---

### Compilation et exécution du serveur

1. **Se déplacer dans le dossier `serveur` :**
   ```bash
   cd serveur
   ```
2. **Compiler le `serveur` :**
   ```bash
   make
   ```
3. **Exécuter le `serveur` :**
   ```bash
   ./serveur
   ```

Le serveur utilise les fichiers suivants pour initialiser les données de l'aquarium : aquarium1.txt et aquarium2.txt.

4. **Load l'aquarium :**
   ```bash
   load aquarium1.txt
   ```

---

### Compilation et exécution du client

1. **Se déplacer dans le dossier `client` :**
   ```bash
   cd client
   ```
2. **Compiler le `client` :**
   ```bash
   make compile
   ```
3. **Créer un package exécutable :**
   ```bash
   make package
   ```
4. **Exécuter le `client` :**
   ```bash
   make run
   ```