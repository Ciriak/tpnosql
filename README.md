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

**3) Lancez à nouveau une instance de mongod mais cette fois, modifiez le dbpath et le
fichier de sortie de logs. Connectez vous sur le shell et affichez les infos utilisées
pour la configuration du processus. Vérifiez aussi que les logs sont bien écrit dans le
fichier avec un tail ­f​ou un cat.​**

```
mongod --logpath /data/log/mongodb.log --dbpath /data/testpath
```

**4) Faites l’import des données contenues dans le fichier zip donnée par l’enseignant
afin de construire une base de données appelé “music”​**

```
mongoimport --db dbname --collection music --drop --file mymusic/songs.metadata.json
```

##Partie 2

**1) Affichez les documents de la collection songs.**

```
show collections
```

**2) Comptez le nombre de documents existants dans la collection songs.**

```
db.songs.count()
```

**3) Affichez exclusivement les titres des chansons du Coldplay de l’album X&Y**

```
db.songs.find(
   {
     artist: "Coldplay",
     album: "X&Y"
   },
   { title: 1 }
)
```

**4) Affichez le titre et album des chansons de Stromae, ordonnés par année de la plus
récente à la plus ancienne, et triés par ordre alphabétique par titre**

```
db.songs.find(
   {
     artist: "Stromae"
   },
   { title: 1,
    album:1}
).sort({
  year : 1
})
```

**5) Affichez les chansons du group Coldplay dans un tableau, où les éléments sont des
strings ayant comme format TITRE (ALBUM). La sortie doit être comme ça : (voir PDF)**

```
db.songs.find(
   {
     artist: "Coldplay",
     album: "X&Y"
   }
)
```

**6) Affichez, une seule fois, le noms des artistes ayant produit des chansons entre 2002
et 2005**

**7) Créez une collection recordLabel, qui puisse stocker maximum 3 documents ou 1 KB
et dont la structure doit être : (voir PDF)**

**8) Insérez les 3 registres dans la collection. Qu’est­ce qui se passe lorsque vous
essayez insérer un 4ème ?**

**9) Modifiez le validator sur la collection afin d’ajouter le pays en utilisant le code (ISO
3166­1 alpha­2)**

**10) Pour allez plus loin**
- a. Qu’est ce que le TTL ?

Le TTL est un délais d'expiration pour les données (time to live)

- b. Quelles sont les modifications à faire sur une collection pour rajouter du TTL
?

Il faut rajouter un index et spécifier le TTL

```
db.log_events.createIndex( { "createdAt": 1 }, { expireAfterSeconds: 3600 } )
```

- c. Si vous devez faire cette manipulation sur la collection recordLabel, il faudrait
faire quoi exactement ?
- d. Créez une nouvelle collection recordLabel2, avec le même validator, mais
avec une TTL sur les documents de 10 secondes.

