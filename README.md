# FlaUI.Window.Extensions

Playwright-style locators, auto-waiting actions, and state queries for FlaUI.

## Getting Started

Install the package:

```bash
dotnet add package FlaUI.Window.Extensions
```

## Usage

```csharp
using FlaUI.Core;
using FlaUI.UIA3;
using FlaUI.Window.Extensions;

var app = Application.Launch("notepad.exe");
var window = app.GetMainWindow(new UIA3Automation());

// Find by AutomationId
window.FindElement("TextEditor").Fill("Hello from FlaUI");

// Find by text
window.GetByText("File").Click();

// Wait for element
window.GetByTestId("SaveButton").WaitFor(WaitForState.Visible);

// Chain locators
window.FindElement("Toolbar").GetByRole(FlaUI.Core.Definitions.ControlType.Button, "Save").Click();

// Type and press
window.FindElement("TextEditor").Type("Hello").Press(FlaUI.Core.WindowsAPI.VirtualKeyShort.RETURN);
```

## License

MIT
