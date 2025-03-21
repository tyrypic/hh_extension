```diff
+------------------+       +---------------------+
|   Chrome         |       |   Bitrix Integration|
|   Extension      |       |   App               |
|                  |       |                     |
|  +------------+  |       |  +---------------+  |
|  |   Auth     |◄-code----►|  | Code Generator|  |
|  |  Manager   |  |       |  +---------------+  |
|  +-----┬------+  |       |                     |
|        │         |       |                     |
+--------┼---------+       +---------------------+
         │
         ▼
+------------------+
|   HH.ru Tab      |
|                  |
|  +------------+  |
|  | Resume Page|  |
|  |  [IMPORT]◄─┼──cookie sync──┐
|  +------------+  |            │
+------------------+            │
                                ▼
+------------------+       +---------------------+
|   Backend        |       |   Bitrix24          |
|   Service        |       |                     |
|                  |       |                     |
|  +------------+  |       |  +---------------+  |
|  | API        |───resume+code──► Create Deal|  |
|  | Endpoint   |◄───────────────┤             |  |
|  +------------+  |       |  +---------------+  |
+------------------+       +---------------------+
```
