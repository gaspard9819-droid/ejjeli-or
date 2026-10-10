# Éjjeli Őr

iPhone-on futó webapp éjszakai recepcióhoz. A telefon hátlapi kamerájával nézi a
biztonsági kamerák monitorát, és **csengőhanggal riaszt**, ha embert lát valamelyik
kijelölt (kritikus) kamerakép-zónában.

**Megnyitás:** https://gaspard9819-droid.github.io/ejjeli-or/ (Safariban)

## Mit tud

- 1–2 zóna kijelölése ujjal a monitor képén (pl. két egymás melletti kamerakép)
- Fektetett telefonra szabott elrendezés: balra a kép, jobbra a gombok
- Emberfelismerés (TensorFlow.js, COCO-SSD) helyben, a telefonon. Kép nem megy ki sehova
- Azonnali riasztás az első találatra, fél másodpercenkénti ellenőrzéssel (állítható)
- Barátságos csengőhang; 30 mp után sűrűbben szól, ha nem állítod le
- Külön (lefelé lépő) hibahang, ha a kép megáll vagy egy percig fekete (kikapcsolt monitor, elmozdult telefon)
- Jobb felső sarokban **Rögzít** gomb: 5 mp visszaszámlálás (közben leteheted a telefont), utána indul az őrzés, és egy rövid jelzőhang igazolja. Ugyanez a gomb **Leállít**
- Élő diagnosztika a kép alatt: zónánként a legjobb emberfelismerési érték és a mozgás mértéke, így látod, miért riaszt vagy miért nem
- Kiegészítő mozgásjelzés (kikapcsolható): a zaj- és fényerő-változásra érzéketlen, pixelenként tanuló érzékelő
- Sötét kijelző mód: fekete képernyő, a figyelés közben is megy
- Napló pillanatképekkel. A téves riasztások megjelölhetők
- Állítható érzékenység, gyakoriság, szünet riasztás után

## Használat előtt

1. Telefon töltőre, **fektetve**, a hátlapi kamera a monitorra néz. Az elforgatás zárolása legyen kikapcsolva, a zónákat fektetett telefonnal rajzold be. Ha a telefon később elfordul, az app hibahanggal szól
2. A némító kapcsoló kikapcsolva, a hangerő maximumon
3. Beállítások → Kijelző és fényerő → Automatikus zárolás → Soha
4. Ne válts más appra, és ne zárd le a telefont: az iPhone ilyenkor leállítja a kamerát
5. Ajánlott: Irányított hozzáférés (Kisegítő lehetőségek)

## Képminőség

A felismerés a monitor képéből dolgozik, ezért a legfontosabb a **méret**: a telefon kerüljön olyan közel, hogy a két kritikus kamerakép kitöltse a kameraképet (a monitor többi része ne legyen benne). Mérés szerint (szimulált, rossz minőségű képen) a modell akkor találja meg az embert, ha a kamerakép-csempén legalább kb. 50–60 pixel magas. 40 pixel alatt már semmilyen beállítás nem segít, ott csak a telefon közelebb vitele.

## Korlátok

- Segédeszköz, nem garancia: kicsi vagy takarásban lévő alakot elnézhet
- Zárolt képernyővel vagy háttérben nem figyel (iOS-korlát). Visszatéréskor kiírja, mennyi ideig nem figyelt
- Első indításkor internet kell a felismerő modell letöltéséhez

## Felépítés

Egyetlen `index.html`, build nélkül. A GitHub Pages a `main` ág gyökeréből szolgálja ki.
