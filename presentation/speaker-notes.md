# Five-minute demo: speaking notes

Use `demo.pptx` for editable slides or `demo.pdf` for a portable version. The seven slides have the same layout and text. PowerPoint also contains these speaker notes.

## 1. The question

This began as a question about how many Christian denominations Wikidata contains. We narrowed it to something we could actually inspect: how 19 selected church bodies are classified. Sixteen match the chosen denomination path and three do not. The point is to understand the modeling behind those results, rather than treat the query as an authority on what counts as a church. The sample is deliberately selected, not representative of the whole database.

## 2. From counting to a manageable sample

We first tried classification-based counts. The page records 1,367 direct instances and 1,670 when subclasses are included. Then we tried religion or worldview, which returned 388,732 items. A type breakdown on QLever had 2,330 distinct types. That is not a denomination list: church buildings and other kinds of entities are included. These are different queries and endpoint snapshots, not additive numbers or a strict funnel. We therefore selected 19 bodies and inspected the statements themselves. See queries 01 through 04 and the preserved exploration tables.

## 3. What the path means

Query 05 starts with each selected item and follows instance of into the class hierarchy. It then follows zero or more subclass of steps until Christian denomination. Zero means a direct instance already matches. Presbyterian Church in America is a direct example. Church of Scotland matches through national Church, and also through state church in the inspected hierarchy. The query uses best-ranked statements. This test is about the existence of a particular recorded path, not an independent judgment about church identity.

## 4. What the sample returned

The results have 33 church-type rows but only 19 churches, because several churches have multiple types. Fifteen match directly and Church of Scotland matches through its types. Free Methodist Church and Lutheran Church of Australia have the broader religious denomination type. Being a religious denomination does not entail being in its Christian subclass. EFCA returns religious organization. The Lutheran church’s own website describes it as a Christian denomination, making it a concrete candidate for a referenced, more specific classification. These are retrieval gaps for this path; changes still require checking the item’s scope.

## 5. The modeling issues are different kinds of issues

EFCA demonstrates a rank effect: a normal-ranked Protestant church type disappears from the direct wdt results because religious organization is preferred. Our supporting rank query found that neither type has the required subclass path, so changing rank alone would not repair the missed match. Other cases are questions rather than established errors. Does Anglican Church of South India adequately name a united church? What scale does church congregation have when used for the Catholic Church? Conversely, being both an organization and a denomination can be perfectly compatible. We should not flatten all differences into the same problem.

## 6. The limitation test

We tested subclass of alone, requiring at least one step. None of our 19 matches that route, so it does not recover the three missed records. Across Wikidata, it finds 58 additional items that do not match the original instance-based path. Some are categories, such as national Church and state church. Others are named candidates, such as World Mission Society Church of God. We cannot add 58 to a denomination total without checking which items are classes, particular bodies, or something else. This is why a broader query is a discovery tool, not automatically a better count.

## 7. Where the investigation leads

The defensible conclusion is that retrieval is sensitive to representation. Even in this selected sample, we see broader and narrower types, rank effects, and scope questions. We have not established a worldwide count, measured how common these patterns are, or shown that every difference is a defect. Next I would inspect the extra 58 candidates and the alternative classifications already listed in the exploratory tables. Names and aliases can be another discovery route, but having denomination in a label would not be sufficient evidence. The open research question is how to distinguish legitimate institutional diversity from modeling choices that make relevant bodies difficult to discover. For a live demo, show query 05, then query 06, then the first few results of query 07.

## Optional live demonstration (another 2–3 minutes)

1. Open [Wikidata Query Service](https://query.wikidata.org/).
2. Paste [query 05](../queries/05-selected-19-classifications.rq). Explain why 33 rows represent 19 churches.
3. Paste [query 06](../queries/06-selected-19-path-comparison.rq). Compare the two Boolean columns.
4. Paste [query 07](../queries/07-subclass-only-candidates.rq). Point out a category and a named body; ask whether both belong in the same count.

If the endpoint times out or today’s data has changed, use the recorded outputs in `../results/` and identify their dates explicitly. Do not present older counts as live results.

Sources: the [full README](../README.md) contains all tables, item revision links, external references, and limitations. The source page is linked on the final slide. This deck summarizes the recorded investigation; it does not add a new population estimate.
