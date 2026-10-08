# Éjjeli Őr

iPhone-on futó webapp éjszakai recepcióhoz. A telefon hátlapi kamerájával nézi a
biztonsági kamerák monitorát, és **hangos szirénával riaszt**, ha embert lát valamelyik
kijelölt (kritikus) kamerakép-zónában.

**Megnyitás:** https://gaspard9819-droid.github.io/ejjeli-or/ (Safariban)

## Mit tud

- 1–2 zóna kijelölése ujjal a monitor képén
- Emberfelismerés (TensorFlow.js, COCO-SSD) helyben, a telefonon. Kép nem megy ki sehova
- Riasztás csak 2 egymás utáni találat után (állítható), ezzel szűri a téves jelzéseket
- Külön hibahang, ha a kép megáll vagy egy percig fekete (kikapcsolt monitor, elmozdult telefon)
- Sötét kijelző mód: fekete képernyő, a figyelés közben is megy
- Napló pillanatképekkel. A téves riasztások megjelölhetők
- Állítható érzékenység, gyakoriság, szünet riasztás után

## Használat előtt

1. Telefon töltőre, a hátlapi kamera a monitorra néz
2. A némító kapcsoló kikapcsolva, a hangerő maximumon
3. Beállítások → Kijelző és fényerő → Automatikus zárolás → Soha
4. Ne válts más appra, és ne zárd le a telefont: az iPhone ilyenkor leállítja a kamerát
5. Ajánlott: Irányított hozzáférés (Kisegítő lehetőségek)

## Korlátok

- Segédeszköz, nem garancia: kicsi vagy takarásban lévő alakot elnézhet
- Zárolt képernyővel vagy háttérben nem figyel (iOS-korlát). Visszatéréskor kiírja, mennyi ideig nem figyelt
- Első indításkor internet kell a felismerő modell letöltéséhez

## Felépítés

Egyetlen `index.html`, build nélkül. A GitHub Pages a `main` ág gyökeréből szolgálja ki.
