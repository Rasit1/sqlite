**Récupérer tous les albums
      SELECT * FROM albums;

**Récupérer tous les albums dont le titre contient "Great" (indice)
      SELECT * FROM albums WHERE Title LIKE '%Great%';

**Donner le nombre total d'albums contenus dans la base (sans regarder les id bien sûr)
      SELECT COUNT * FROM albums;

**Supprimer tous les albums dont le nom contient "music"
      DELETE FROM albums WHERE Title LIKE '%music%';

**Récupérer tous les albums écrits par AC/DC
      SELECT * FROM albums JOIN artists ON albums.ArtistId = artists.ArtistId WHERE artists.Name = "AC/DC";

**Récupérer tous les titres des albums de AC/DC
  SELECT albums.Title FROM albums JOIN artists ON albums.ArtistId = artists.ArtistId WHERE artists.Name = "AC/DC";

**Récupérer tous les titres des albums de AC/DC (get all the titles of the all the albums of AC/DC)

  SELECT
      trackid,
      tracks.name AS track,
      albums.title AS album,
      artists.name AS artist
  FROM
  tracks
      INNER JOIN albums ON albums.AlbumId = tracks.AlbumId
      INNER JOIN artists ON artists.ArtistId = albums.ArtistId WHERE artists.Name LIKE "AC/DC" ;

**Récupérer la liste des titres de l'album "Let There Be Rock"
  SELECT
      tracks.name AS title,
      albums.title AS album
  FROM
      tracks
      JOIN albums ON albums.AlbumId = tracks.AlbumId WHERE albums.Title LIKE "Let There Be Rock";

**Afficher le prix de cet album ainsi que sa durée totale
  SELECT
      tracks.UnitPrice AS price,
      SUM(tracks.Milliseconds) AS total_duration
  FROM
      tracks
      INNER JOIN albums ON albums.AlbumId = tracks.AlbumId WHERE albums.Title LIKE "Let There Be Rock";

**Afficher le coût de l'intégralité de la discographie de "Deep Purple"
  SELECT
      SUM(tracks.UnitPrice) As total_price
  FROM
      tracks
      INNER JOIN albums ON albums.AlbumId = tracks.AlbumId
      INNER JOIN artists ON artists.ArtistId = albums.ArtistId WHERE artists.Name LIKE "Deep Purple";

**Créer l'album de ton artiste favori en base, en renseignant correctement les trois tables albums, artists et tracks

  SELECT Name FROM albums, artists, tracks WHERE artists.Name Like "Eric Clapton";
