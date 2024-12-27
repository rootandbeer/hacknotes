---
title: Shells
tags:
  - MOC
  - Shells
category:
  - MOC
  - Shells
share: true
date: 2024-12-15
---

```dataviewjs
let tags = await dv.pages('#shells').groupBy(p => p.file.tags[0].split('/')[1]);

tags.forEach(tag => {
    // Start the callout with the correct title
    let calloutContent = `> [!note]- ## ${tag.key}\n`;

    // Add the file links inside the callout
    calloutContent += tag.rows.map(row => `> - [[${row.file.name}]]`).join("\n");

    // Output the callout content as one block
    dv.paragraph(calloutContent);
});

```