## Why do we need to use weak pointer sometimes?

Issue: shared\_ptr circular referencing



"Weak\_ptr" is called "weak" because it points to a shared instance without incrementing the instance reference counter. Conversely, a "shared\_ptr" is "strong" because it increments such counter.

