```
using System;
using UnityEngine;

public class WaitForSecondsOrButtonSkip : CustomYieldInstruction
{
    private float waitTime;
    private bool isMouse;
    private int mouseButtonIndex;
    private KeyCode keyCode;

    public override bool keepWaiting
    {
        get
        {
            return Time.time < waitTime && !(isMouse ? Input.GetMouseButtonUp(mouseButtonIndex) : Input.GetKeyUp(keyCode));
        }
    }

    public WaitForSecondsOrButtonSkip(float time, bool isMouse = true, int mouseButtonIndex = 0, KeyCode keyCode = KeyCode.Escape)
    {
        waitTime = Time.time + time;
        this.isMouse = isMouse;
        this.mouseButtonIndex = mouseButtonIndex;
        this.keyCode = keyCode;
    }
}
```
