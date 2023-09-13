# phroni

PH Reliable Object Notation Insight, a generic visualization library for electronic business documents.
Thanks to Elisabeth, Neele, Moritz and Thomas for helping coming up with this name.

The visualization of business documents is a tedious task, because it involves a lot of different parameterization and customizations in all areas of the process. Because the visualized document is often misunderstood as the original, even though it is "just" a different kind of display of an "original" that is present in a different structured, machine readable format only.

The main steps of the visualization process are:
1. Have a valid source document, in a strucutred source format. *phroni* initially only supports XML based source formats.
2. Convert the source format into one of the supported destination formats (e.g. HTML, PDF, AsciiDoc, ...). This process requires parameters based on the selected transformation (e.g. XSLT parameters) as well as basic output definition parameters like the result language/locale. In case it is deemed technically reasonable, the usage of multiple such transformation steps (with or without post processing steps) might be queued
3. Post processing 
    * Eventually based on the source format
    * Restricted to a specific destination format
    * Zero, one or multiple post processing steps might be queued
    * Only predefined post processing steps will be allowed, because they require programming. An API for custom post processing plugins will be made available as well to implement custom post processing rules.
4. declarative orchestration of the visualization steps, to ensure the results are deterministic and reliable
