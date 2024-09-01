# Shapely

**Shapely** on Python teek, mis pakub lihtsat ja tõhusat viisi geomeetriliste andmete töötlemiseks ja analüüsimiseks. See teek on ideaalne tööriist 2-D andmete, näiteks punktide, joonte ja polügoonide loomiseks, manipulatsiooniks ja analüüsimiseks.

## Põhiomadused

- **Geomeetriliste Objektide Loomine**: Looge ja manipuleerige erinevaid geomeetrilisi objekte nagu punktid, jooned ja polügoonid.
- **Geomeetrilised Operatsioonid**: Teostage lõikepunktide arvutusi, ühendamist, lõikamist ja vahemaade määramist.
- **Kattuvuse ja Sarnasuse Kontrollimine**: Kontrollige, kas geomeetrilised objektid kattuvad, lõikuvad või on teatud kaugusel üksteisest.
- **Integreerimine Muudega**: Töötab hästi koos teiste geoinfosüsteemide tööriistadega nagu GeoPandas.









# --- Shapely Meetodite Loetelu ---

# Geomeetria loomine
from shapely.geometry import Point, LineString, Polygon, MultiPoint, MultiLineString, MultiPolygon, GeometryCollection

# Geomeetrilised operatsioonid
from shapely.ops import unary_union, nearest_points, cascaded_union, split, snap, linemerge

# --- Geomeetrilised Meetodid ---

# Intersect/Union/Distance
intersect = geom1.intersection(geom2)      # Leiab kahe geomeetria lõikepunkti
union = geom1.union(geom2)                 # Leiab kahe geomeetria ühenduse
difference = geom1.difference(geom2)       # Leiab geomeetrilise erinevuse
symmetric_difference = geom1.symmetric_difference(geom2)  # Leiab sümmeetrilise erinevuse
distance = geom1.distance(geom2)           # Arvutab kahe geomeetria vahelise kauguse

# Lihtsustamine ja simplifikatsioon
simplified = geom.simplify(tolerance)      # Lihtsustab geomeetriat määratud tolerantsiga

# Kõveruste ja piiride arvutamine
length = line.length                       # Arvutab joone pikkuse
area = polygon.area                        # Arvutab polügooni pindala
boundary = geom.boundary                   # Tagastab geomeetria piiri kui joon

# Kontrollpunktid geomeetrias
contains = geom1.contains(geom2)           # Kontrollib, kas geom1 sisaldab geom2
within = geom1.within(geom2)               # Kontrollib, kas geom1 on geom2 sees
crosses = geom1.crosses(geom2)             # Kontrollib, kas geom1 ristub geom2-ga
touches = geom1.touches(geom2)             # Kontrollib, kas geom1 puutub geom2
overlaps = geom1.overlaps(geom2)           # Kontrollib, kas geom1 kattub geom2-ga
equals = geom1.equals(geom2)               # Kontrollib, kas geom1 on geom2-ga võrdne
disjoint = geom1.disjoint(geom2)           # Kontrollib, kas geom1 ja geom2 on lahus

# --- Transformatsioonid ---

from shapely.affinity import scale, rotate, translate

# Skaaleerimine (mastaapimine)
scaled_geom = scale(geom, xfact=2, yfact=1, origin='center')  # Skaaleerib geom 2x laiemaks ja ei muuda kõrgust

# Pööramine
rotated_geom = rotate(geom, angle=45, origin='centroid')      # Pöörab geom-i 45 kraadi ümber tsentroidi

# Nihutamine (transleerimine)
translated_geom = translate(geom, xoff=10, yoff=5)            # Nihutab geom-i 10 ühikut paremale ja 5 ühikut üles

# --- Täpsemad Operatsioonid ja Kontrollid ---

# Kõige lähemate punktide leidmine
nearest_pt = nearest_points(geom1, geom2)                     # Leiab geom1 ja geom2 kõige lähemad punktid

# Geomeetria lõhkumine
split_geom = split(geom, cutter)                              # Lõikab geom teise geomeetriaga (nt joon)

# Liitmine
merged_geom = linemerge([line1, line2])                       # Liidab kaks või enam joont üheks

# Snap ehk täpsuse parandamine
snapped_geom = snap(geom1, geom2, tolerance)                  # Snäpib geom1 geom2-le määratud tolerantsusega

# Mitmete geomeetrite liitmine
united_geom = unary_union([geom1, geom2, geom3])              # Liidab mitu geomeetriat üheks

# --- Muud Meetodid ---

# Katvus (buffer)
buffered_geom = geom.buffer(distance)                         # Loob geom-i ümber puhvri määratud kaugusega

# Koordinaatide pööramine
rotated_geom = geom.exterior.rotate(angle=90, origin=(0, 0))  # Pöörab geom-i määratud nurga ümber päritolu






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
