# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_060000.jpg
- R6 mid MISSING
- R9 center MISSING
- R10 mid MISSING
## adasind_086220.jpg
- L4+R5 mid WRONG_CLASS
- L5 mid SPURIOUS
- R4 center MISSING
## adasind_102750.jpg
- L1+R4 edge WRONG_CLASS
- L2+R3 mid WRONG_CLASS
- L3 center SPURIOUS
- L5+R2 edge WRONG_CLASS
- R5 center MISSING

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 9 | 6 | 3 | 1 |
| mid | 8 | 4 | 4 | 3 |
| edge | 3 | 1 | 2 | 2 |
