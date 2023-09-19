# phroni

PH Reliable Object Notation Insight, a generic visualization library for electronic business documents.
Thanks to Elisabeth, Moritz, Neele and Thomas for helping coming up with this fabulous name.

The visualization of business documents is a tedious task, because it involves a lot of different parameterization and customizations in all areas of the process. Because the visualized document is often misunderstood as the original, even though it is "just" a different kind of display of an "original" that is present in a different structured, machine readable format only.

The main steps of the visualization process are:
1. Have a valid *source document*, in a strucutred *source format*. *phroni* initially only supports XML based source formats - further source formats may be added later.
2. *Convert* the source format into one of the supported *destination formats* (e.g. HTML, PDF, AsciiDoc, ...). This process requires parameters based on the selected transformation rules (e.g. XSLT parameters) as well as basic output definition parameters like the result language/locale. The rules for transformation should be provided in a declarative fashion (e.g. XSLT), so that they can easily be versioned.
3. *Post processing*. That could be layout changes, watermarking, alteration of security settings (e.g. disallow printing), end user specific logos etc.
    * Restricted to a specific destination format
    * May use data from the source format as input as well.
    * Zero, one or more post processing steps might be executed sequentially (in a micro service way of thinking)
    * Should be able to use the source format and the target format to perform its actions. If multiple transformations are performed, only the first source format (the *original source format*) will be provided.
    * Only predefined post processing steps will be allowed, because they require programming. An API for custom post processing plugins will be made available as well to implement custom post processing rules.
4. In case it is deemed technically reasonable, the usage of multiple such transformation phases (conversion + post processing) steps (with or without post processing steps) might be queued. That could end in a workflow like convert A to B, post process B, convert B to C, post process C1, post process C2
5. Declarative orchestration of the visualization steps, to ensure the results are deterministic and reliable. The orchestration steps should be made available as structured data so they can be versioned like the rules themselves.
6. Transformation rules and Orchestration descriptors should be retrievable from external sources.

