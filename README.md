# titlesanditems
Titles and Items Report (Sierra)

Open PG Admin
Connect to server (sierra db)
Open SQL Editor

SELECT 
  i.agency_code_num                    AS Agency_num, 
  an.name                         AS Agency,
  COUNT (DISTINCT bil.bib_record_id)            AS Title_Count,
  COUNT (DISTINCT i.record_id)                AS Item_Count
FROM 
  sierra_view.item_record                 AS i
  RIGHT JOIN sierra_view.bib_record_item_record_link     AS bil
     ON (bil.item_record_id = i.id)
  JOIN sierra_view.agency_property             AS ap
     ON (ap.code_num = i.agency_code_num)
  JOIN sierra_view.agency_property_name         AS an
     ON (an.agency_property_id = ap.id)
GROUP BY 1,2
ORDER BY 2
;

In Create Lists do the following search for total titles in database:
BIBLIOGRAPHIC Material Type not equal to 1
AND BIBLIOGRAPHIC Material Type not equal to x
AND BIBLIOGRAPHIC Material Type not equal to t
AND BIBLIOGRAPHIC Material Type not equal to k
