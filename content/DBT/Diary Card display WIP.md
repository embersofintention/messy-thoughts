```dataview

TABLE WITHOUT ID 
date as "Date and Time",
tags as "tags",
file.frontmatter as "yeehaw",
track_joy as "joyfulness (0-10)",
track_sorrow as "sorrow (0-10)",
track_guilt as "guilt (0-10)",
track_shame as "shame (0-10)",
track_anger as "anger (0-10)”,
track_anxiety as "anxiety (0-10)"



FROM #diary-card AND !"_Templates" AND !"index"
SORT date-sketched, ASC

WHERE file.name != this.file.name
FLATTEN choice(typeof(img)="link",
    embed(link(meta(
        choice(
            typeof(img)="link",
                img, this.file.link
        )
    ).path, "250")), "![](" + img + ")") AS EmbededCoverImg


```