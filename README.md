<div align="center">

## A simple window


</div>

### Description

It's a simple blank window that you can resize.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[kenshin](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/kenshin.md)
**Level**          |Beginner
**User Rating**    |4.0 (12 globes from 3 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__3-3.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/kenshin-a-simple-window__3-10097/archive/master.zip)

### API Declarations

&lt;windows.h&gt;


### Source Code

```
#include <windows.h>
LRESULT CALLBACK WindowProcedure (HWND, UINT, WPARAM, LPARAM);
char szClassName[ ] = "WindowsApp";
int WINAPI WinMain (HINSTANCE hThisInstance,
          HINSTANCE hPrevInstance,
          LPSTR lpszArgument,
          int nFunsterStil)
{
  HWND hwnd;
  MSG messages;
  WNDCLASSEX wincl;
  /* The Window structure */
  wincl.hInstance = hThisInstance;
  wincl.lpszClassName = szClassName;
  wincl.lpfnWndProc = WindowProcedure;
  wincl.style = CS_DBLCLKS;
  wincl.cbSize = sizeof (WNDCLASSEX);
  wincl.hIcon = LoadIcon (NULL, IDI_APPLICATION);
  wincl.hIconSm = LoadIcon (NULL, IDI_APPLICATION);
  wincl.hCursor = LoadCursor (NULL, IDC_ARROW);
  wincl.lpszMenuName = NULL;
  wincl.cbClsExtra = 0;
  wincl.cbWndExtra = 0;
  wincl.hbrBackground = (HBRUSH) COLOR_BACKGROUND;
  if (!RegisterClassEx (&wincl))
    return 0;
  hwnd = CreateWindowEx (
      0,
      szClassName,
      "Windows App",
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT,
      CW_USEDEFAULT,
      544,
      375,
      HWND_DESKTOP,
      NULL,
      hThisInstance,
      NULL
      );
  ShowWindow (hwnd, nFunsterStil);
  while (GetMessage (&messages, NULL, 0, 0))
  {
    TranslateMessage(&messages);
    DispatchMessage(&messages);
  }
  return messages.wParam;
}
LRESULT CALLBACK WindowProcedure (HWND hwnd, UINT message, WPARAM wParam, LPARAM lParam)
{
  switch (message)
  {
    case WM_DESTROY:
      PostQuitMessage (0);
      break;
    default:
      return DefWindowProc (hwnd, message, wParam, lParam);
  }
  return 0;
}
```

