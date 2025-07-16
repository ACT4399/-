# Ackermann 函數作業報告（遞迴版本）

---

## 一、解題說明

### 問題描述

Ackermann 函數是一個在理論計算機科學中非常著名的遞迴函數，其增長速度遠超一般多項式或指數函數。它是一個非原始遞迴（non-primitive recursive）的例子，常用來測試程式語言的遞迴能力與執行效率。

Ackermann 函數的定義如下：


本題目要求使用遞迴方式實作 Ackermann 函數，並根據使用者輸入的 m 與 n 輸出對應的結果。

### 🧭 解題策略

- 使用純遞迴依定義實作 Ackermann 函數。
- 實作 `ackermann(int m, int n)` 函數並處理三種情況。
- 注意不要輸入過大的 m 與 n，以避免堆疊溢位（stack overflow）。

---

## 二、程式實作

### ✅ 限用標頭：

```cpp
#include <iostream>
using namespace std;
#include <iostream>
using namespace std;

int ackermann(int m, int n) {
    if (m == 0)
        return n + 1;
    else if (n == 0)
        return ackermann(m - 1, 1);
    else
        return ackermann(m - 1, ackermann(m, n - 1));
}

int main() {
    int m, n;
    cout << "Enter m and n: ";
    cin >> m >> n;
    cout << "Ackermann(" << m << ", " << n << ") = " << ackermann(m, n) << endl;
    return 0;
}
## 三、效能分析（Performance Analysis）

### ⏱ 時間複雜度（Time Complexity）

Ackermann 函數的時間複雜度極高，因為每一次遞迴都可能展開成多層次的遞迴樹。其增長速度超過指數級，屬於超原始遞迴級別。

- **時間複雜度：** `O(A(m, n))`  
  （其中 A 為 Ackermann 函數自身，代表其運算次數接近 A(m, n) 本身的大小）

> 例如：A(3, 3) = 61 → 需要呼叫超過 60 層次的遞迴。

---

### 💾 空間複雜度（Space Complexity）

- **遞迴版本空間複雜度：** `O(A(m, n))`  
  遞迴函數每呼叫一次就壓入一次堆疊，因此呼叫層數等同於使用的堆疊記憶體深度，最壞情況空間複雜度與時間相同。

---

## 四、測試與驗證

| 測試案例 | 輸入參數 (m, n) | 預期輸出 | 實際輸出 |
|----------|------------------|----------|----------|
| 測試一   | (0, 0)           | 1        | 1        |
| 測試二   | (1, 1)           | 3        | 3        |
| 測試三   | (2, 2)           | 7        | 7        |
| 測試四   | (3, 3)           | 61       | 61       |
| 測試五   | (3, 4)           | 125      | 125      |

> ⚠️ 注意：`m = 4` 或以上會導致極高的計算與記憶體需求，容易導致 stack overflow。

---

## 五、申論與開發報告

### 💡 為何使用遞迴？

- Ackermann 函數本身是遞迴定義，直接使用遞迴實作能清楚對應數學定義。
- 程式碼簡潔易懂，適合作為學習遞迴與堆疊成長的案例。
- 可讓開發者理解遞迴深度與程式語言堆疊限制之間的關係。

### ⚠️ 限制與建議

- 遞迴版本在 m 和 n 過大時容易造成記憶體堆疊溢位（Stack Overflow）。
- 若需處理大輸入，可考慮使用非遞迴實作或限制輸入範圍（如 m ≤ 3）。

---
