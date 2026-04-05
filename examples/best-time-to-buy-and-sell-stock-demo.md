# 📖 Example Walkthrough: Best Time to Buy and Sell Stock (LeetCode #121)

This document demonstrates a complete interaction — from the initial structured
overview to the Socratic dialogue phase.

---

## Student Input

```
Please teach me Best Time to Buy and Sell Stock — LeetCode #121
```

---

## AI Tutor — First Response (Fixed Structured Format)

### 📋 Problem Analysis

#### 🔍 Rule Explanation

- **Input:** An integer array `prices` where `prices[i]` is the stock price on day `i`
- **Output:** The maximum profit you can achieve; return `0` if no profit is possible
- **Constraints:** You may only complete **one transaction** (buy once, sell once);
  you must buy before you sell
- **Key restriction:** `buy_day < sell_day`

```
Example: prices = [ppl-ai-file-upload.s3.amazonaws](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/16381573/f531a001-5bb7-45cd-930e-9340cdf4580d/two-sum-demo.md?AWSAccessKeyId=ASIA2F3EMEYEW5H446VK&Signature=I4EconBhkX8cIxLFivdefhVgr5w%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEOX%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJIMEYCIQDGkejkhLei96r9RNn%2FmgytLiiBg4sRLY4OrneYcJvOeAIhAP%2FrISENGJxR56jkO5fVfpSfZszIN0GqNAjpD7qm4DL7KvwECK7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQARoMNjk5NzUzMzA5NzA1Igwc8k%2FkxIA5W0wPGroq0ASzrSxRrUYIFqtExXJ27Y59GiwDorb9Dllhxf%2BSeY3GorEn9nATM3NWhcEUchWb6L2qAd4%2FhUc653UdBYhw2vGV7%2F1VZzWiV7pAaRZd4E5yQGOfuUN0L7Qd5EByXSVER%2BhI1MkelLNMIzHfGxCeskJyzvrQWbmZTCzvn2q7e5d%2FXhRXvZozIXyTcaN%2FJaY87RfSdAOvRDxSSXcLl7Qwr4SD1A%2Fn3%2BgV6j4lkMDNfHr8q3HiCfCUeHLTCWkpc3Z1QTRrUYx9oi3X4PXKzF63vOSE7P9Mm7rMzzXt%2FhozTX%2Bn98cUcRF4OSPer7G%2BfxxQpKl%2F9b4Asci5%2FFW0%2BsC8B0XxPp%2BLbU6Rl082tDPrSChCRTlfhtRegd92PnqQ6YRQ6y3N3Rath2hrKW3N5lmDLmpwwJVQrEGBSvtxx8QfqGxtY%2BIp%2ByqrJB5f7EyKcD%2FHGlKYE5UMfSmtnDY8aB3XYsr0OEHr4c1hTNbBIv%2FCrqKnqY5f7Zd1dTxa64iEvU7m7VXAYD8gTfVLxqBK1w9kuug81neVFrXx7evDVoQzgfbM%2BZaeexm9FzdZ34qZDxMyllQIUrESNUAYRBQT0laEbIiRs6a4xc8vHn1qfhYZ0PCmV%2FMyuOhAoFX9tPGwXiVavFk%2Byh0eCgHXRkHsru9J%2BIjvjo4xp2xqMu6puDmHCpKyDweu%2FhqLk3S3Krn08mzrmyEVDoDdz25TnmUGM5fkbPZuhlDpGbiRTazfNmnhLfc2RrQ%2F1tTxmT1TTvW%2B0%2FmU8ygJ14mX%2BRfVm4cuUDFHuvlSMMPWx84GOpcB5eYw3gO9z9N6E92TM0GF7MmBbwWzSgAr9i398g8iiKUQCuYc7EH%2B9x%2FdmMysE4ISLeVTu8ZSGe6eeIvYceE17QLr8F69lGiZZYWcTTu8iNaXW2%2F50G5GZ2KJaSpZMdP7oUfpZz%2BHv7pFeaXbiB4pzWkTH%2FwPXtcc79tMLIciY6Qy81nZSNnhsqJWrTAhSQzXS8XC18us4w%3D%3D&Expires=1775367630)
Output:  5   // Buy on day 1 (price=1), sell on day 4 (price=6)
```

#### 💡 Core Concepts

- **Single-pass greedy** — track the minimum price seen so far and update max
  profit on every step
- **"Valley before peak" intuition** — profit is maximized when you buy at the
  lowest valley and sell at the highest subsequent peak
- **Why sorting/brute-force fails** — sorting destroys the time ordering constraint

#### ⭐ Importance Assessment

| Dimension | Assessment |
|-----------|-----------|
| Interview frequency | ⭐⭐⭐⭐⭐ Ubiquitous — appears in nearly every company's easy/medium bank |
| Difficulty | Easy |
| Learning value | 🔑 Foundation for all sliding-window and "running min/max" patterns |
| Transferability | Very high — direct parent of #122, #123, #188, #309 |

---

### 🛠️ Core Algorithm & Data Structure

**Running Minimum + Single Pass**

- **Two variables only:** `min_price` (best buy seen so far) and `max_profit`
- **Update rule:** At each day `i`:
  1. `min_price = min(min_price, prices[i])`
  2. `max_profit = max(max_profit, prices[i] - min_price)`
- **Why this is correct:** Every sell candidate `prices[i]` is paired with the
  cheapest possible buy day that came before it — the global best is never missed.

---

### 🎯 Solution Strategies & Comparison

| Approach Type | Time Complexity | Space Complexity | Pros | Cons |
|---------------|-----------------|------------------|------|------|
| Brute Force (nested loops) | O(N²) | O(1) | Trivial to understand | Times out on large inputs |
| **Single-pass greedy (optimal)** | **O(N)** | **O(1)** | One pass, constant space | Requires the "running min" insight |

> The sort + two-pointer approach **does not apply** here because sorting would
> destroy the chronological buy-before-sell constraint.

---

### 🔗 Related Problems & Extended Concepts

**Best Time to Buy and Sell Stock family:**
- #122 — Unlimited transactions (greedy, sum all upward slopes)
- #123 — At most 2 transactions (DP)
- #188 — At most k transactions (DP generalization)
- #309 — With cooldown (DP with state machine)

**Extended concepts to explore:**
- Kadane's Algorithm — #121 is structurally equivalent to Maximum Subarray (#53)
  on the difference array `prices[i] - prices[i-1]`
- Sliding window minimum for multi-day windows

---

### ⚠️ Common Mistakes & Pitfalls

1. **Selling before buying** — Forgetting the `buy_day < sell_day` constraint
   and accidentally computing a negative profit as valid
2. **Initializing `min_price = 0`** — Should be `prices[0]` or `float('inf')`;
   zero is not a valid price floor
3. **Returning negative profit** — Always floor `max_profit` at `0`
4. **Confusing this with #122** — Here you get exactly one transaction,
   not unlimited; the greedy "sum all gains" trick from #122 is wrong here

---

**Follow-up from tutor (end of structured overview):**

> That's the full landscape of this problem. Which part would you like to explore first?
>
> - **A)** 🧠 Why does tracking `min_price` guarantee we never miss the optimal buy day?
> - **B)** 💻 Walk through the implementation line by line
> - **C)** ⚡ Interview recap mode — give me the code skeleton and the one-sentence takeaway

---

## Socratic Dialogue Phase (Student picks A)

**Student:** I'll go with A.

**Tutor:**

> Great — let's build the intuition before touching code.
>
> Picture yourself watching stock prices tick by on a screen, one day at a time.
> You can't see tomorrow's price — only today's and everything before it.
>
> Each day you ask yourself two questions:
> 1. "Is today's price cheaper than anything I've seen before?"
>    → If yes, **this is my new potential buy day**.
> 2. "If I sell today, what profit would I make against the cheapest buy I've recorded?"
>    → If it beats my current best profit, **update the record**.
>
> Here's the key insight: you never need to go back and re-examine old prices.
> Once a new minimum appears, every future sell will naturally pair with it
> instead of the old minimum — because it's cheaper.
>
> **So here's the question for you:** Suppose `prices = [7, 1, 5, 3, 6, 4]`.
> Walk me through the value of `min_price` and `max_profit` after processing
> **just the first three days** (prices 7, 1, 5). What do you get? 🤔

*(The tutor waits for the student's response before continuing.)*

---

## 🔑 One-Sentence Key Takeaway

*Triggered after the student successfully formulates the optimal solution:*

> **#121 in one sentence:** Scan once — keep a running `min_price` as your
> "best buy so far" and update `max_profit = max(max_profit, price - min_price)`
> at every step; the answer accumulates itself.

---

## Reference Code (shown only after student-led implementation)

```python
def maxProfit(prices: list[int]) -> int:
    min_price = float('inf')
    max_profit = 0
    for price in prices:
        min_price  = min(min_price, price)       # cheapest buy seen so far
        max_profit = max(max_profit, price - min_price)  # best profit if selling today
    return max_profit
```