# Networking Basics #1

## Description
Ce projet approfondit les concepts réseaux avec des exercices pratiques sur la configuration IP et la gestion des connexions.

## Objectifs d'apprentissage

### Configuration IP et Réseau
* Comprendre localhost (127.0.0.1)
* Comprendre l'adresse 0.0.0.0
* Comprendre le fichier /etc/hosts
* Savoir afficher les interfaces réseau actives

## Fichiers et leurs fonctionnalités

### 0-change_your_home_IP
Script qui configure un serveur Ubuntu avec les exigences suivantes :
* localhost résout vers 127.0.0.2
* facebook.com résout vers 8.8.8.8

### 1-show_attached_IPs
Script qui affiche toutes les adresses IPv4 actives sur la machine où il est exécuté.

### 2-port_listening_on_localhost
Script qui met en place un serveur d'écoute sur le port 98 de localhost :
* Utilise netcat pour créer le serveur
* Peut recevoir et afficher des messages des clients
* Utile pour le débogage de connexions réseau

## Usage
1. Les scripts doivent être rendus exécutables : `chmod +x script_name`
2. Exécution avec sudo pour les scripts nécessitant des privilèges : `sudo ./script_name`
3. Pour le script d'écoute de port, utiliser telnet dans un autre terminal pour tester : `telnet localhost 98`

## Note
Pour le script 0-change_your_home_IP, attention à bien restaurer la configuration originale de localhost (127.0.0.1) après les tests pour éviter des problèmes de fonctionnement.