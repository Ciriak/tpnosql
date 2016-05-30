# TP NoSQL
Réponses aux questions du TP NO SQL

##Partie 1
**1) Vérifiez qu'aucun processus mongo tourne actuellement sur votre machine. Si c’est
le cas, arretez­le. Ensuite lancez une instance mongod avec le dbpath par défaut.
Connectez­vous sur le shell mongo et affichez le port utilisé et less infos du host
depuis le shell.**

```
mongod
```

**2) Arretez le processus depuis le shell.**

```
mongod --shutdown
```

**3)Lancez à nouveau une instance de mongod mais cette fois, modifiez le dbpath et le
fichier de sortie de logs. Connectez vous sur le shell et affichez les infos utilisées
pour la configuration du processus. Vérifiez aussi que les logs sont bien écrit dans le
fichier avec un tail ­f​ou un cat.​**

```
mongod --logpath /data/log/mongodb.log --dbpath /data/testpath
```

**4)Faites l’import des données contenues dans le fichier zip donnée par l’enseignant
afin de construire une base de données appelé “music”​**

```
mongoimport --db dbname --collection music --drop --file mymusic/songs.metadata.json
```
