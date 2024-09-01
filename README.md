# Shapely

**Shapely** on Python teek, mis pakub lihtsat ja tõhusat viisi geomeetriliste andmete töötlemiseks ja analüüsimiseks. See teek on ideaalne tööriist 2-D andmete, näiteks punktide, joonte ja polügoonide loomiseks, manipulatsiooniks ja analüüsimiseks.

## Põhiomadused

- **Geomeetriliste Objektide Loomine**: Looge ja manipuleerige erinevaid geomeetrilisi objekte nagu punktid, jooned ja polügoonid.
- **Geomeetrilised Operatsioonid**: Teostage lõikepunktide arvutusi, ühendamist, lõikamist ja vahemaade määramist.
- **Kattuvuse ja Sarnasuse Kontrollimine**: Kontrollige, kas geomeetrilised objektid kattuvad, lõikuvad või on teatud kaugusel üksteisest.
- **Integreerimine Muudega**: Töötab hästi koos teiste geoinfosüsteemide tööriistadega nagu GeoPandas.





# Shapely Meetodite Loetelu

## Geomeetria Loomine

```python
from shapely.geometry import (
    Point, LineString, Polygon, MultiPoint,
    MultiLineString, MultiPolygon, GeometryCollection
)






# Shapely Meetodite Loend

Shapely teek pakub mitmekesiseid meetodeid geomeetriliste objektide töötlemiseks ja analüüsimiseks. Allpool on toodud peamised meetodid koos lühikeste selgitustega, sealhulgas keerukamate ja transformatsiooni meetoditega.

## **Punktide Meetodid**

- **`Point(x, y)`**  
  Loob punkt-objekti antud koordinaatidega `(x, y)`.

- **`distance(other)`**  
  Arvutab kauguse praeguse punkti ja `other` geomeetria vahel.

- **`within(other)`**  
  Kontrollib, kas punkt asub `other` geomeetria sees.

## **Joonte Meetodid**

- **`LineString(coordinates)`**  
  Loob joon-objekti antud koordinaatide loendi põhjal.

- **`length`**  
  Tagastab joonise pikkuse.

- **`intersection(other)`**  
  Leiab lõikepunktid praeguse joone ja `other` geomeetria vahel.

- **`buffer(distance)`**  
  Loob joonise ümbermõõdu määratud kaugusel, laiendades joonise äärist.

- **`simplify(tolerance)`**  
  Lihtsustab joone kuju, kasutades määratud taluvust, vähendades joonise punkte.

## **Polügoonide Meetodid**

- **`Polygon(coordinates)`**  
  Loob polügooni-objekti antud koordinaatide loendi põhjal.

- **`area`**  
  Tagastab polügooni pindala.

- **`perimeter`**  
  Tagastab polügooni ümbermõõdu.

- **`contains(other)`**  
  Kontrollib, kas polügoon sisaldab `other` geomeetria.

- **`intersection(other)`**  
  Leiab lõikepunktid polügooni ja `other` geomeetria vahel.

- **`difference(other)`**  
  Eemaldab `other` geomeetria polügoonist, andes jääkosa.

- **`union(other)`**  
  Ühendab polügooni `other` geomeetriaga, luues uue geomeetria.

- **`sym_difference(other)`**  
  Leiab kahe geomeetria sümmeetrilise erinevuse.

- **`simplify(tolerance)`**  
  Lihtsustab polügooni kuju, vähendades polügooni punktide arvu määratud taluvuse alusel.

## **Üldised Meetodid**

- **`is_empty`**  
  Kontrollib, kas geomeetria on tühi (ei sisalda andmeid).

- **`bounds`**  
  Tagastab geomeetria piiride neliku (vasak, all, parem, ülemine).

- **`exterior`**  
  Tagastab polügooni välimise äärise geomeetria.

- **`interiors`**  
  Tagastab kõik polügooni sisemised äärised (aukude korral).

- **`representative_point()`**  
  Tagastab esinduspunkti, mis asub geomeetria sees.

- **`wkt`**  
  Tagastab geomeetria Well-Known Text (WKT) formaadis.

- **`geojson`**  
  Tagastab geomeetria GeoJSON formaadis.

## **Transformatsiooni Meetodid**

- **`shapely.ops.transform(func, *geometries)`**  
  Rakendab transformatsioonifunktsiooni `func` ühele või mitmele geomeetriaobjektile.

- **`shapely.ops.affine_transform(matrix, *geometries)`**  
  Rakendab afiintransformatsiooni antud afiinimaatri abil.

- **`shapely.ops.cascaded_union(geometries)`**  
  Ühendab mitu geomeetriaobjekti ühte geomeetriaobjekti, et luua ühtne geomeetria.

- **`shapely.ops.unary_union(geometries)`**  
  Ühendab geomeetriaobjektide loendi, käsitledes neid kui ühte objektide kogumit.

## **Näited**

```python
from shapely.geometry import Point, LineString, Polygon
from shapely.ops import transform

# Punkt
p = Point(1, 1)
print(p.distance(Point(2, 2)))  # Arvutab kauguse

# Joon
line = LineString([(0, 0), (1, 1), (2, 2)])
print(line.length)  # Tagastab joone pikkuse

# Polügoon
poly = Polygon([(0, 0), (1, 0), (1, 1), (0, 1)])
print(poly.area)  # Tagastab polügooni pindala

# Joonise ümbermõõdu loomine
buffered_line = line.buffer(1)
print(buffered_line)  # Loob joonise ümbermõõdu

# Geomeetria transformatsioon
def rotate(x, y):
    return x, y + 1

rotated_line = transform(rotate, line)
print(rotated_line)  # Rakendab pööramist
