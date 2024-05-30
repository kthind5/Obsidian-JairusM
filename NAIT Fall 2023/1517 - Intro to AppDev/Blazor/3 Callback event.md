---
tags:
  - Blazor
  - CPSC1517
  - Csharp
---

[[2023-10-04]]

A callback is a reference to an executable code that is passed as an argument. In Blazor, this can be done when embedding pages in each other. 

OnDataSent is a callback `EventCallBack<T>`

A callback event can be contained in some of the razor pages that are used. For example, a file that can be embedded required a parameter by having the following parameters: 
```csharp
[Parameter] public string DataToSend( { get; set; }
[Parameter] public EventCallback<string> OnDataSent { get; set; }

private void TextProcessing()
{
	//feedback is filled then feedback fills DataToSend
	DataToSend = feedback = $"Email {emailText} -- Password {passwordText} --  DateTime {datetimeText.ToShortDateString()}";
	//evokes the EventCallback
	OnDataSent.InvokeAsync(DataToSend);
}
```

When embedding this razor page in another razor page, it requires the callback function. It is shown below: 

```csharp
<ControlsTextBoxes OnDataSent="HandleDataSent"></ControlsTextBoxes>
@ code {
	private void HandleDataSent(string data)
}
```

![[1 Blazor introduction#Cool things to know]]
