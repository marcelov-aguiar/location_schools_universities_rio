# Sobre o projeto
O objetivo desse projeto simples é exibir em um mapa do OpenStreetMapa localização das escolas e universidades da cidade do Rio de Janeiro (Brasil). Aqui será usado Leaflet (plugin MakerCluster) integrado com OpenStreetMap.

# Dados
Os dados da localização e descrição das escolas e univerdades do Rio de Janeiro fora obtidas no site do Overpass. Pode ser encontrado no seguinte link: https://overpass-turbo.eu/.


## Query para procurar escolas
```
[out:json][timeout:600];
//[out:csv(::lat,::lon,::type,"name")];
// gather results
{{geocodeArea:Rio de Janeiro}}->.searchArea;
(
  // query part for: “amenity=school”
  node[amenity=school](area.searchArea);
  way[amenity=school](area.searchArea);
  relation[amenity=school](area.searchArea);
);
// print results
out body;
>;
out skel qt;
```

## Query para procurar universidades
```
[out:json][timeout:600];
//[out:csv(::lat,::lon,::type,"name")];
// gather results
{{geocodeArea:Rio de Janeiro}}->.searchArea;
(
  // query part for: “amenity=school”
  node[amenity=university](area.searchArea);
  way[amenity=university](area.searchArea);
  relation[amenity=university](area.searchArea);
);
// print results
out body;
>;
out skel qt;
```

# Referências
- https://overpass-turbo.eu/.
- https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_API_by_Example#Banks_far_away_from_police_stations
- https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dschool
- https://stackoverflow.com/questions/31046501/how-to-get-points-from-openstreetmap-of-a-certain-country