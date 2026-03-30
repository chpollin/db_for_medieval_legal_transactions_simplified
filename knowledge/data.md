# Data Description

## Quellensammlung

10 TEI-XML-Dokumente aus QGW II/1 (Quellen zur Geschichte der Stadt Wien, Bd. II/1). Alle aus dem Wiener Stadt- und Landesarchiv, Hauptarchiv Urkunden. Schema: RelaxNG (`sources/schema/toolbox.rng`).

## Dokumenteninventar

| Nr. | Datum | Transaktionstyp | Personen | Orgs | roleName-Typen |
|-----|-------|-----------------|----------|------|----------------|
| 1 | [1198–1230] | gegeben (Schenkung) | 3 | 1 | kin |
| 2 | 1. H. 13. Jh. | verkauft | 4 | 1 | kin |
| 3 | 1239 | gibt (Seelenheil) | 1 | 1 | — |
| 10 | 1274 | gibt (Rente) | 2 | 1 | occ, kin |
| 20 | 1292-06-05 | bezeugt, gewidmet | 3 | 2 | occ |
| 30 | 1301-10-14 | verleiht (Ablass) | 1 | 2 | occ |
| 50 | 1311-05-30 | verkaufen | 3 | 1 | occ, kin |
| 80 | 1320-07-11 | bezeugen, verpflichten | 4 | 1 | occ, title, dead |
| 100 | 1327-09-29 | verkaufen (Haus) | 7 | 1 | kin, title |
| 110 | 1328-05-01 | bestätigen, setzen (Pfand) | 4 | 1 | kin, title |

## Register (Subsets)

- `indices/personList.xml` — 30 Personen (Subset aus 16.088 im Gesamtbestand)
- `indices/orgList.xml` — 7 Organisationen (Subset aus 1.078)
- `indices/placeList.xml` — leer (Orte werden in diesen Dokumenten über `<roleName type="topo">` referenziert, nicht über `<rs type="place">`)

## Raw-Dokument (Workshop-Aufgabe)

- `raw/120_plaintext.txt` — Plaintext-Transkription von QGW II/1, Nr. 120 (1330)
- Bestätigungsurkunde: Abt und Konvent der Schotten bestätigen eine Stiftung
- Enthält: 5 Personen, 1 Organisation, roleName-Typen occ, kin, dead, title
- Aufgabe: In TEI-XML konvertieren nach dem Annotationsmodell in `edition.md`

## TEI-Dokumentstruktur

Jedes Dokument folgt dieser Grundstruktur:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE TEI SYSTEM "../../../schema/toolbox_full.dtd">
<TEI xmlns="http://www.tei-c.org/ns/1.0">
  <teiHeader>
    <fileDesc>
      <titleStmt><title>...</title></titleStmt>
      <publicationStmt><p/></publicationStmt>
      <sourceDesc>
        <bibl type="url">https://www.monasterium.net/...</bibl>
        <bibl>Quellen zur Geschichte der Stadt Wien, Bd. II/1, Nr. ...</bibl>
        <msDesc>
          <msIdentifier>
            <repository>Wiener Stadt- und Landesarchiv</repository>
            <idno>...</idno>
          </msIdentifier>
          <physDesc><sealDesc>...</sealDesc></physDesc>
        </msDesc>
      </sourceDesc>
    </fileDesc>
    <profileDesc>
      <creation>
        <date when="...">...</date>
        <origDate>...</origDate>
      </creation>
    </profileDesc>
  </teiHeader>
  <facsimile>
    <surface><graphic url="..."/></surface>
  </facsimile>
  <text>
    <body>
      <div type="abstract" resp="...">
        <!-- Annotierter Regesttext -->
      </div>
      <div type="seal">
        <!-- Siegelbeschreibung -->
      </div>
      <div type="lists">
        <!-- xi:include-Referenzen auf Register -->
      </div>
    </body>
  </text>
</TEI>
```

## Faksimile-Bilder

Jedes Dokument verlinkt auf Digitalisate des Wiener Stadt- und Landesarchivs via monasterium.net (recto + verso). Die URLs sind im `<facsimile>`-Element hinterlegt.
