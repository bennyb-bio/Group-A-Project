# Projekt Gruppe A Vergleich und Integration von Codierungssystemen im klinischen Kontext (ICD vs. SNOMED CT vs. LOINC)

Group for " Datenmanagement &amp; Archivierung im Umfeld der Forschung"

## Einleitung

## Methoden
**Vorgehen**
- Erarbeitung theoretischer Grundlagen zu ICD, SNOMED-CT und LOINC
- Analyse der zur Verfügung gestellten CSV-Dateien
- Fokusierung auf die Dateien patients.csv, conditions.csv, observations.csv
- Formulierung der Forschungsfrage "Inwiefern kann ein vereinfachtes Mapping zwischen ICD, LOINC und SNOMED CT dazu beitragen, die Konsistenz und Wiederverwendbarkeit klinischer Daten zu verbessern?
"
- Erstellung von Mapping-Tabellen mittels KI-Unterstützung (map_snomed_icd.csv, map_loinc_snomed.csv
- Coding ist in Google Colaboratory erfolgt
- Auswertung der Daten mittels Google Colaboratory
- Prüfung der Datenvalidierung und -qualität in Google Colaboratory
- Beantwortung der Forschungsfrage

**Coding**
- verwendete Bibliotheken: sqlite3, pandas, numpy, os, matplotlib.pyplot
- Einlesen der Dateien map_snomed_icd und map_loinc_snomed.csv in pandas-Data-Frame
- 


## Flowchart Mapping COVID ICD-10

```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#075189',
      'primaryTextColor': '#fff',
      'secondaryColor': '#5496BF',
      'secondaryBorderColor': '#075189'
    }
  }
}%%
graph TD;
  labor[Existing Labor Test Loinc];
  labor -- yes --- value;
  value[Value of laboratoy test];
  labor -- no --> symptoms;
  symptoms[Check Symptoms];
  value -- positive --- U701G;
  value -- not detected --- symptoms;
  symptoms -- sepcific symptom x, y or death certificate --- specific;
  symptoms -- unspecific symptoms ---unspecific;
  specific["`Specific Symptoms or Death
               check Snomed`"];
  specific -- snomed = 4 and not snomed = 6 --- U702V;
  specific -- snomed = 6 --- U702G;
  specific -- else ---nocovid;
  symptoms -- no symptoms ---nocovid;
  unspecific["`Unspecific Symptoms
               check Snomed`"];
  unspecific -- snomed = 4 or snomed = 6 ---U701V;
  unspecific -- else ---nocovid;
  nocovid[[No Covid]];
  U701G[[U701G]];
  U702G[[U702G]];
  U702V[[U702V]];
  U701V[[U701V]];
```

## Ergebnisse

## Diskussion

### International harmonisierte Daten-Qualitätsstandards

**Definition der drei Hauptkategorien der Datenqualität (Michael G. Kahn et al., 2016):**

1. **Konformität (Conformance)**: Übereinstimmung der Daten mit festgelegten Standards.
2. **Vollständigkeit (Completeness)**: Ausmaß, in dem alle erforderlichen Daten vorhanden sind.
3. **Plausibilität (Plausibility)**: Glaubwürdigkeit und logische Konsistenz der Daten.

| **Kategorie nach Kahn et al.**         | **Datenqualitäts Punkt**                         | **Relevanz** |
|--------------------------------------|--------------------------------|------------------------------------------------------|
| **Conformance (Übereinstimmung)** | Ungemappte Daten | Fehlende Übereinstimmung mit Standards → erschwert Verifikation |
| | Konsistentes Mapping | Einheitliche Kodierung notwendig für interne und externe Validierung |
| | Richtige Formatierung (SNOMED-CT, ICD-10, LOINC) | Korrekte Anwendung erleichtert Verifikation & Validierung |
| **Plausibility (Plausibilität)** | Dublettenkennung | Doppelte Einträge beeinträchtigen Glaubwürdigkeit der Daten |
| **Completeness (Vollständigkeit)** | Liegt eine Beschreibung vor (ICD-10)? | Fehlende Beschreibungen erschweren Verifikation und Validierung |
| | Hat jeder LOINC-Code einen Laborwert? | Fehlende Werte beeinträchtigen die Datenvollständigkeit und deren klinische Nutzbarkeit |



## Perspektive
