---
name: Feature request
about: Suggest an idea for this project
title: ''
labels: ''
assignees: ''

---

Thanks for submitting a feature request for **Scriptable Callbacks Pipeline**!
Please provide as much detail as you can so we can evaluate, discuss, and (hopefully) add the enhancement.

## ★ Proposed functionality  
_A concise description of the new capability._

> Example  
> “Add a `Throttle(seconds)` observer-logic wrapper that suppresses events if they fire faster than the given interval.”

---

## Optional – How it might be implemented  
_Please share any architectural or API ideas you have.  
Code sketches, flow diagrams or pseudocode are welcome._

<details>
<summary>Click to expand</summary>

```csharp
// e.g. extend SubscriptionLogicBase<T> …

public sealed class ThrottleLogic<T> : SubscriptionLogicBase<T>
{
    public float Interval;
    float _nextAllowedTime;

    public override InvokationResult OnPreInvoke(ref T arg)
    {
        if (Time.time < _nextAllowedTime) return InvokationResult.Skip;
        _nextAllowedTime = Time.time + Interval;
        return InvokationResult.Continue;
    }
}
```
</details>

---

## Optional – How this can be useful
_Explain your own use case or give an example of how proposed feature
can impact overall experience for other users._
