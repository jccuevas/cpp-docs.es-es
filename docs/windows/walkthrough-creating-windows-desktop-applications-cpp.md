---
title: 'Tutorial: Crear una aplicación tradicional de escritorio de Windows (C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: cb6d09acc00f2e38ee41180c81c1877bc53027c2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037967"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Tutorial: Crear una aplicación tradicional de escritorio de Windows (C++)

Este tutorial muestra cómo crear una aplicación de escritorio tradicional de Windows en Visual Studio. Creará la aplicación de ejemplo usa la API de Windows para mostrar "Hola, escritorio de Windows" en una ventana. Puede utilizar el código que va a desarrollar en este tutorial como modelo para crear otras aplicaciones de escritorio de Windows.

La API de Windows (también conocida como la API Win32, API de escritorio de Windows y API clásica de Windows) es un marco basada en el lenguaje C para crear aplicaciones de Windows. Ha estado en existencia desde la década de 1980 y se ha usado para crear aplicaciones de Windows durante décadas. Marcos de trabajo más avanzadas y más fácil de programa se han creado sobre la API de Windows, como MFC, ATL y .NET frameworks. Código más moderna para las aplicaciones para UWP y Store escritas en C++ / c++ / WinRT usa la API de Windows debajo. Para obtener más información acerca de la API de Windows, consulte [Windows API Index](/windows/desktop/apiindex/windows-api-list). Hay muchas maneras de crear aplicaciones de Windows, pero el proceso descrito anteriormente fue el primero.

> [!IMPORTANT]
> Por brevedad, se omiten algunas instrucciones de código en el texto. El [compilar el código](#build-the-code) sección al final de este documento muestra el código completo.

## <a name="prerequisites"></a>Requisitos previos

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Se recomienda Windows 10 para una mejor experiencia de desarrollo.

- Una copia de Visual Studio 2017. Para obtener información sobre cómo descargar e instalar Visual Studio, consulte [instalar Visual Studio](/visualstudio/install/install-visual-studio). Al ejecutar el programa de instalación, asegúrese de que el **desarrollo de escritorio con C++** está activada la carga de trabajo. No se preocupe si no ha instalado esta carga de trabajo al instalar Visual Studio. Puede ejecutar de nuevo el instalador y lo instale ahora.

   ![Desarrollo de escritorio con C++](../build/media/desktop-development-with-cpp.png "desarrollo de escritorio con C++")

- Comprensión de los aspectos básicos del uso de IDE de Visual Studio. Si ha usado las aplicaciones de escritorio de Windows antes, probablemente puede mantenerse al día. Para obtener una introducción, consulte [Guía de características del IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Comprensión de lo suficiente los aspectos básicos del lenguaje C++ para seguir el tutorial. No se preocupe, no hacemos algo muy complicado.

## <a name="create-a-windows-desktop-project"></a>Crear un proyecto de escritorio de Windows

Siga estos pasos para crear su primer proyecto de escritorio de Windows y escriba el código para una aplicación de escritorio de Windows en funcionamiento. Si usa una versión de Visual Studio anteriores a Visual Studio 2017 versión 15.3, vaya a [para crear un proyecto de escritorio de Windows en Visual Studio 2017 RTM](#create-in-vs2017-rtm).

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Para crear un proyecto de escritorio de Windows en Visual Studio 2017 Update 15.3 y versiones posteriores

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el cuadro de diálogo **nuevo proyecto**, en el panel izquierdo, expanda **instalado** > **Visual C++**, a continuación, seleccione **Windows Desktop**. En el panel central, seleccione **Asistente de escritorio de Windows**.

   En el **nombre** , escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Aceptar**.

   ![Denomine el proyecto DesktopApp](../build/media/desktop-app-new-project-name-153.png "denomine el proyecto DesktopApp")

1. En el cuadro de diálogo **proyecto de escritorio de Windows**, en **tipo de aplicación**, seleccione **aplicación de Windows (.exe)**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Aceptar** para crear el proyecto.

   ![Crear DesktopApp en el Asistente para proyecto de escritorio de Windows](../build/media/desktop-app-new-project-wizard-153.png "crear DesktopApp en el Asistente para proyecto de escritorio de Windows")

1. En **el Explorador de soluciones**, haga clic en el **DesktopApp** del proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**. En el **nombre** , escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop.cpp*. Haga clic en **Agregar**.

   ![Archivo .cpp de agregar al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "archivo .cpp de agregar al proyecto DesktopApp")

Ya se ha creado el proyecto y se abre el archivo de origen en el editor. Para continuar, puede ir directamente a [crear el código](#create-the-code).

### <a id="create-in-vs2017-rtm"></a> Para crear un proyecto de escritorio de Windows en Visual Studio 2017 RTM

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el cuadro de diálogo **nuevo proyecto** cuadro de diálogo, en el panel izquierdo, expanda **instalado** > **plantillas** > **Visual C++** y, a continuación, seleccione **Win32**. En el panel central, seleccione **Proyecto Win32**.

   En el **nombre** , escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Aceptar**.

   ![Denomine el proyecto DesktopApp](../build/media/desktop-app-new-project-name-150.png "denomine el proyecto DesktopApp")

1. En la página **Introducción** del **Asistente para aplicaciones Win32**, elija **siguiente**.

   ![Crear DesktopApp en Introducción al Asistente para aplicaciones Win32](../build/media/desktop-app-win32-wizard-overview-150.png "crear DesktopApp en Introducción al Asistente para aplicaciones Win32")

1. En la pagina **configuración de la aplicación**, en **tipo de aplicación**, seleccione **aplicación Windows**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **finalizar** para crear el proyecto.

   ![Crear DesktopApp en el Asistente para configuración de la aplicación de Win32](../build/media/desktop-app-win32-wizard-settings-150.png "crear DesktopApp en el Asistente para configuración de la aplicación de Win32")

1. En **el Explorador de soluciones**, haga clic en el proyecto DesktopApp, elija **agregar**y, a continuación, elija **nuevo elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**. En el **nombre** , escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop.cpp*. Haga clic en **Agregar**.

   ![Archivo .cpp de agregar al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "archivo .cpp de agregar al proyecto DesktopApp")

Ya se ha creado el proyecto y se abre el archivo de origen en el editor.

## <a name="create-the-code"></a>Crear el código

A continuación, obtendrá información sobre cómo crear el código para una aplicación de escritorio de Windows en Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Para iniciar una aplicación de escritorio de Windows

1. Al igual que cada aplicación de C y de C++ deben tener una función `main`  como punto de partida, cada aplicación de escritorio de Windows debe tener una función `WinMain` . `WinMain` tiene la siguiente sintaxis.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Para obtener información sobre los parámetros y el valor devuelto de esta función, vea [punto de entrada WinMain](/windows/desktop/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > ¿Cuáles son todas esas palabras adicionales, como `CALLBACK`, o `HINSTANCE`, o `_In_`? La API de Windows tradicional usa definiciones de tipos y macros de preprocesador ampliamente para abstraer algunos de los detalles de los tipos y específicos de la plataforma de código, como convenciones de llamada, **__declspec** declaraciones e instrucciones pragma del compilador. En Visual Studio, puede usar IntelliSense [información rápida](/visualstudio/ide/using-intellisense#quick-info) característica para ver lo que definen estas definiciones de tipos y macros. Mantenga el mouse sobre la palabra de interés, o selecciónelo y presione **Ctrl**+**K**, **Ctrl**+**me** para un pequeña ventana emergente que contiene la definición. Para obtener más información, vea [Usar IntelliSense](/visualstudio/ide/using-intellisense). A menudo usan parámetros y tipos de valor devuelto *anotaciones SAL* que le ayudarán a los errores de programación de catch. Para obtener más información, consulte [utilizar anotaciones SAL para reducir defectos de código de C o C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Programas de escritorio de Windows requieren &lt;windows.h >. &lt;Tchar.h > define el `TCHAR` macro, que se resuelve en última instancia a **wchar_t** si el símbolo UNICODE está definido en el proyecto, en caso contrario, se resuelve como **char**.  Si compila siempre con habilitada para UNICODE, no necesita TCHAR y puede usar simplemente **wchar_t** directamente.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Además de la función `WinMain` , todas las aplicaciones de escritorio de Windows deben tener una función de procedimiento de ventana. Esta función normalmente se denomina `WndProc` , pero puede asignarle el nombre que prefiera. `WndProc` tiene la siguiente sintaxis.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   En esta función, escribe código para controlar *mensajes* que recibe la aplicación de Windows cuando *eventos* se producen. Por ejemplo, si un usuario elige un botón Aceptar en la aplicación, Windows enviará un mensaje a usted y puede escribir código dentro de su `WndProc` función que hace que sea adecuado. Se llama *control* un evento. Solo controlar los eventos que son relevantes para su aplicación.

   Para más información, vea [Procedimientos de ventanas](/windows/desktop/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Para agregar funcionalidad a la función WinMain

1. En el `WinMain` función, rellenar una estructura de tipo [WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa). La estructura contiene información acerca de la ventana, por ejemplo, el icono de aplicación, el color de fondo de la ventana, el nombre para mostrar en la barra de título y lo que es importante, un puntero de función para el procedimiento de ventana. El ejemplo siguiente muestra una estructura típica de `WNDCLASSEX` .

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   Para obtener información acerca de los campos de la estructura anterior, consulte [WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa).

1. Registrar el `WNDCLASSEX` con Windows para que sepa que TI acerca de la ventana y cómo enviar mensajes a ella. Use la función [RegisterClassEx](/windows/desktop/api/winuser/nf-winuser-registerclassexa) y pase la estructura de clase de ventana como argumento. El `_T` macro se usa porque usamos el `TCHAR` tipo.

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. Ahora puede crear una ventana. Use la función [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) .

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   Esta función devuelve un `HWND`, que es un identificador a una ventana. Un identificador es un poco como un puntero que Windows usa para realizar un seguimiento de ventanas abiertas. Para obtener más información, vea [Tipos de datos de Windows](/windows/desktop/WinProg/windows-data-types).

1. En este momento, la ventana se ha creado pero todavía es necesario indicar a Windows para que sea visible. Eso es lo que hace este código:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   La ventana que se muestra no tiene mucho contenido porque todavía no ha implementado la `WndProc` función. En otras palabras, la aplicación aún no está controlando los mensajes de Windows ahora está enviando a él.

1. Para controlar los mensajes, primero se agregue un bucle de mensajes para que escuche los mensajes que envía Windows. Cuando la aplicación recibe un mensaje, este bucle lo envía a su `WndProc` función para que lo administre. El bucle de mensajes es similar al código siguiente.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Para más información sobre las estructuras y funciones que se usan en el bucle de mensajes, vea [MSG](/windows/desktop/api/winuser/ns-winuser-msg), [GetMessage](/windows/desktop/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).

   En este punto, la función `WinMain` debe ser similar al código siguiente.

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>Para agregar funcionalidad a la función WndProc

1. Para habilitar la función `WndProc` a fin de controlar los mensajes que recibe la aplicación, implemente una instrucción switch.

   Es un mensaje importante para controlar el [WM_PAINT](/windows/desktop/gdi/wm-paint) mensaje. La aplicación recibe el `WM_PAINT` mensaje cuando forma parte de su ventana mostrada debe actualizarse. El evento puede producirse cuando un usuario mueve una ventana delante de la ventana, a continuación, mueve inmediatamente a intentarlo, y no sabe la aplicación cuando se producen estos eventos. Sólo Windows sabe, por lo que le notifica con `WM_PAINT`. Cuando la ventana se muestra por primera vez, todas del mismo deben actualizarse.

   Para controlar un mensaje `WM_PAINT` , primero llame a [BeginPaint](/windows/desktop/api/winuser/nf-winuser-beginpaint), controle toda la lógica para mostrar el texto, los botones y otros controles de la ventana y luego llame a [EndPaint](/windows/desktop/api/winuser/nf-winuser-endpaint). Para la aplicación, la lógica entre la llamada inicial y la llamada final consiste en mostrar la cadena "Hola, escritorio de Windows" en la ventana. En el siguiente código, observe que la función [TextOut](/windows/desktop/api/wingdi/nf-wingdi-textouta) se usa para mostrar la cadena.

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC` en el código es un identificador de un contexto de dispositivo, que es una estructura de datos que Windows usa para habilitar la aplicación para comunicarse con el subsistema de gráficos. El `BeginPaint` y `EndPaint` funciones que la aplicación se comporte como un buen ciudadano y no usa el contexto de dispositivo durante más tiempo de lo que necesita. Las funciones ayude a que el subsistema de gráficos está disponible para su uso por otras aplicaciones.

1. Una aplicación normalmente controla muchos otros mensajes, por ejemplo, [WM_CREATE](/windows/desktop/winmsg/wm-create) cuando se crea una ventana por primera vez, y [WM_DESTROY](/windows/desktop/winmsg/wm-destroy) cuando se cierra la ventana. El código siguiente muestra una función `WndProc` básica pero completa.

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>Compilar el código

Como hemos dicho, este es el código completo de la aplicación de trabajo.

### <a name="to-build-this-example"></a>Para compilar este ejemplo

1. Eliminar cualquier código que ha escrito en *HelloWindowsDesktop.cpp* en el editor. Copie este código de ejemplo y, a continuación, péguelo en *HelloWindowsDesktop.cpp*:

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. En el menú **Compilar** , elija **Compilar solución**. Los resultados de la compilación deben aparecer en el **salida** ventana de Visual Studio.

   ![Compile el proyecto DesktopApp](../build/media/desktop-app-project-build-150.gif "compilar el proyecto DesktopApp")

1. Para ejecutar la aplicación, presione **F5**. Una ventana que contiene el texto "Hola, escritorio de Windows" debe aparecer en la esquina superior izquierda de la pantalla.

   ![Ejecute el proyecto DesktopApp](../build/media/desktop-app-project-run-157.png "ejecutar el proyecto DesktopApp")

¡Enhorabuena! Ha completado este tutorial y creado una aplicación de escritorio de Windows tradicional.

## <a name="see-also"></a>Vea también

[Aplicaciones de escritorio de Windows](../windows/windows-desktop-applications-cpp.md)