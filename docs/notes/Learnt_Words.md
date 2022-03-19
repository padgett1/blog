---
tag: "dashboard"
cssClasses: "table-max row-alt"
share: True
---
# Learnt Words
```dataviewjs
dv.table(
	["Learnt Word", "Meaning", "Date"],
	dv.pages('"50-life/56-daily"')
	.filter(p => p["Learnt Word"])
	.sort(p => dv.date(p.file.name), 'desc')
	.flatMap(p =>
		Array.from(
			{
				length: Math.floor(
					p["Learnt Word"].length / 2
				)
			},
			(_, i) => [
				`${'**'}${p["Learnt Word"][i * 2]}${'**'}`,
				p["Learnt Word"][(i * 2) +1],
				dv.fileLink(
					p.file.name,
					false,
					dv.date(p.file.name)
						.toFormat(dv.settings.defaultDateFormat)
				)
			]
		)
	)
)
```






template: - only works in daily notes
Learnt Word:: "word", "description"