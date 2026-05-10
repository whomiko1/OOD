---
tags: [dashboard]
---

# Dashboard

## 未完成的任務

```dataview
TASK
FROM ""
WHERE !completed
SORT file.mtime DESC
```

## 最近 7 天的筆記

```dataview
TABLE file.mtime AS "最後修改"
FROM "" AND !#dashboard
WHERE file.mtime >= date(today) - dur(7 days)
SORT file.mtime DESC
LIMIT 10
```

## 進行中的專案

```dataview
TABLE deadline AS "截止日期", status AS "狀態"
FROM #project
WHERE status = "active"
SORT deadline ASC
```

## 正在閱讀的書

```dataview
TABLE author AS "作者", rating AS "評分"
FROM #book
WHERE status = "reading"
SORT file.mtime DESC
```

## 本週會議

```dataview
TABLE file.day AS "日期"
FROM #meeting
WHERE file.day >= date(today) - dur(7 days)
SORT file.day DESC
```
