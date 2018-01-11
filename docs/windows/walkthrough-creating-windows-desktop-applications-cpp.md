---
title: "Tutorial: Crear una aplicación de escritorio de Windows tradicional (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 10/09/2017
ms.reviewer: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.assetid: a247a9af-aff1-4899-9577-5f8104a0afbb
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8926e5e2432dea0e366698346df1d4b708517553
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Tutorial: Crear una aplicación de escritorio de Windows tradicional (C++)

Este tutorial muestra cómo crear una aplicación de escritorio tradicional de Windows en Visual Studio. La aplicación de ejemplo que creará usa la API de Windows para mostrar "Hola, el escritorio de Windows." en una ventana. Puede utilizar el código que va a desarrollar en este tutorial como modelo para crear otras aplicaciones de escritorio de Windows.

La API de Windows (también conocido como la API de Win32, API de escritorio de Windows y API clásica de Windows) es un marco de trabajo en función del lenguaje de C para crear aplicaciones de Windows. Ha estado en existencia desde la década de 1980 y se ha utilizado para crear aplicaciones de Windows para décadas. Marcos de trabajo más avanzadas y más fácil de programa se han integrado encima de esta API, como MFC y ATL, versiones de .NET Framework. Código incluso más modernas para UWP y el almacén de aplicaciones escritas en C++ / WinRT usa esta API debajo. Para obtener más información acerca de la API de Windows, vea [índice de la API de Windows](https://msdn.microsoft.com/library/windows/desktop/ff818516.aspx). Hay muchas maneras de crear aplicaciones de Windows, pero esto fue el primero.

> [!IMPORTANT]
> Por brevedad, en el texto se omiten algunas instrucciones de código. El [compilar el código](#build-the-code) sección al final de este documento muestra el código completo.

## <a name="prerequisites"></a>Requisitos previos

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Se recomienda Windows 10 para una mejor experiencia de desarrollo.

- Una copia de Visual Studio de 2017. Para obtener información acerca de cómo descargar e instalar Visual Studio, vea [instalar Visual Studio 2017](/visualstudio/install/install-visual-studio). Al ejecutar el programa de instalación, asegúrese de que el **el desarrollo de escritorio con C++** se comprueba la carga de trabajo. No se preocupe si no instala esta carga de trabajo cuando se instala Visual Studio. Puede ejecutar de nuevo el programa de instalación y lo instale ahora.

   ![Desarrollo de escritorio con C++](../build/media/desktop-development-with-cpp.png "el desarrollo de escritorio con C++")

- Descripción de los fundamentos del uso del IDE de Visual Studio. Si ha usado las aplicaciones de escritorio de Windows antes, probablemente pueden mantenerse al día. Para obtener una introducción, consulte [Guía de características del IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Descripción de suficiente de los fundamentos del lenguaje C++ para seguir el tutorial. No se preocupe, hemos no hacen nada sea muy complicado.

## <a name="create-a-windows-desktop-project"></a>Crear un proyecto de escritorio de Windows

Siga estos pasos para crear su primer proyecto de escritorio de Windows y escriba el código para una aplicación de escritorio de Windows y en funcionamiento. Si usa una versión de Visual Studio anteriores a Visual Studio 2017 versión 15.3, ir directamente a [para crear un proyecto de escritorio de Windows en Visual Studio de 2017 RTM](#create-in-vs2017-rtm).

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Para crear un proyecto de escritorio de Windows en Visual Studio de 2017 actualización 15.3 y versiones posteriores

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el **nuevo proyecto** cuadro de diálogo, en el panel izquierdo, expanda **instalado**, **Visual C++**, a continuación, seleccione **Windows Desktop**. En el panel central, seleccione **Asistente de escritorio de Windows**.

   En el **nombre** , escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Aceptar**.

   ![Denomine el proyecto DesktopApp](../build/media/desktop-app-new-project-name-153.png "denomine el proyecto DesktopApp")

1. En el **proyecto de escritorio de Windows** cuadro de diálogo, en **tipo de aplicación**, seleccione **aplicación de Windows (.exe)**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Aceptar** para crear el proyecto.

   ![Crear DesktopApp en el Asistente para proyecto de escritorio de Windows](../build/media/desktop-app-new-project-wizard-153.png "crear DesktopApp en el Asistente para proyecto de escritorio de Windows")

1. En **el Explorador de soluciones**, haga clic en el **DesktopApp** proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**. En el **nombre** , escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop.cpp*. Haga clic en **Agregar**.

   ![Archivo .cpp de agregar al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "archivo .cpp de agregar al proyecto de DesktopApp")

Ahora se crea el proyecto y el archivo de código fuente se abre en el editor. Para continuar, ir directamente a [crear el código](#create-the-code).

### <a id="create-in-vs2017-rtm"></a>Para crear un proyecto de escritorio de Windows en Visual Studio de 2017 RTM

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el **nuevo proyecto** cuadro de diálogo, en el panel izquierdo, expanda **instalado**, **plantillas**, **Visual C++**y, a continuación, seleccione **Win32**. En el panel central, seleccione **Proyecto Win32**.

   En el **nombre** , escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Aceptar**.

   ![Denomine el proyecto DesktopApp](../build/media/desktop-app-new-project-name-150.png "denomine el proyecto DesktopApp")

1. En el **Introducción** página de la **Asistente para aplicaciones Win32**, elija **siguiente**.

   ![Crear DesktopApp en Introducción al Asistente para aplicaciones Win32](../build/media/desktop-app-win32-wizard-overview-150.png "crear DesktopApp en Introducción al Asistente para aplicaciones Win32")

1. En el **configuración de la aplicación** página, en **tipo de aplicación**, seleccione **aplicación de Windows**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **finalizar** para crear el proyecto.

   ![Crear DesktopApp en el Asistente para configuración de la aplicación de Win32](../build/media/desktop-app-win32-wizard-settings-150.png "crear DesktopApp en configuración del Asistente para aplicaciones Win32")

1. En **el Explorador de soluciones**, haga clic en el proyecto DesktopApp, elija **agregar**y, a continuación, elija **nuevo elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**. En el **nombre** , escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop.cpp*. Haga clic en **Agregar**.

   ![Archivo .cpp de agregar al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "archivo .cpp de agregar al proyecto de DesktopApp")

Ahora se crea el proyecto y el archivo de código fuente se abre en el editor.

## <a name="create-the-code"></a>Crear el código

A continuación, aprenderá a crear el código para una aplicación de escritorio de Windows en Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Para iniciar una aplicación de escritorio de Windows

1. Al igual que cada C y C++ aplicación deben tener un `main` funcionar como punto de partida, todas debe tener la aplicación de escritorio de Windows un `WinMain` función. `WinMain` tiene la siguiente sintaxis.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Para obtener información sobre los parámetros y el valor devuelto de esta función, vea [punto de entrada WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

   > [!NOTE]
   > ¿Cuáles son todas esas palabras adicionales, como **devolución de llamada**, o **HINSTANCE**, o  **\_en\_**? La API de Windows tradicional usa definiciones de tipos y macros de preprocesador ampliamente a condensan y eliminan algunos de los detalles de los tipos y específica de la plataforma de código, como convenciones de llamada, **__declspec** las declaraciones y las directivas pragma de compilador. En Visual Studio, puede usar las características de IntelliSense [Quick Info](/visualstudio/ide/using-intellisense#quick-info) característica para ver qué definen estas definiciones de tipos y macros. Mantenga el mouse sobre la palabra de interés, o selecciónelo y presione ctrl-K, ctrl-I para una pequeña ventana emergente que contiene la definición. Para obtener más información, vea [Usar IntelliSense](/visualstudio/ide/using-intellisense). Parámetros y tipos devueltos a menudo usan *anotaciones SAL* para ayudarle a catch errores de programación. Para obtener más información, consulte [utilizar anotaciones SAL para reducir defectos de código de C o C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Programas de escritorio de Windows requieren &lt;windows.h >. &lt;Tchar.h > define el `TCHAR` (macro), que se resuelve en última instancia a `wchar_t` si el símbolo UNICODE se define en el proyecto, en caso contrario, se resuelve como `char`.  Si siempre se compila con habilitada para UNICODE, no es necesario TCHAR y puede utilizar wchar_t directamente.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Además de la función `WinMain` , todas las aplicaciones de escritorio de Windows deben tener una función de procedimiento de ventana. Esta función se denomina normalmente `WndProc` pero puede dar el nombre quiera. `WndProc` tiene la siguiente sintaxis.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   En esta función se escribe código para controlar *mensajes* que recibe la aplicación de Windows cuando *eventos* se producen. Por ejemplo, si un usuario elige un botón Aceptar en la aplicación, Windows enviará un mensaje a usted y puede escribir código dentro de su `WndProc` función que realiza la operación que sea adecuada. Esto se denomina *control* un evento. Solo controlar los eventos que son relevantes para la aplicación.

   Para obtener más información, consulte [procedimientos de ventana](https://msdn.microsoft.com/library/windows/desktop/ms632593).

### <a name="to-add-functionality-to-the-winmain-function"></a>Para agregar funcionalidad a la función WinMain

1. En el `WinMain` función, rellenar una estructura de tipo [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577). Esta estructura contiene información acerca de la ventana, por ejemplo, el icono de la aplicación, el color de fondo de la ventana, el nombre para mostrar en la barra de título y lo que es muy importante, un puntero a función para el procedimiento de ventana. El ejemplo siguiente muestra una estructura típica de `WNDCLASSEX` .

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

   Para obtener información acerca de los campos de esta estructura, vea [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577).

1. Debe registrar el `WNDCLASSEX` con Windows para que sepa que TI acerca de la ventana y cómo enviar mensajes a ella. Use la [RegisterClassEx](https://msdn.microsoft.com/library/windows/desktop/ms633587) función y pase la estructura de clase de ventana como argumento. El `_T` macro se usa porque usamos el `TCHAR` tipo.

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

1. Ahora puede crear una ventana. Use la [CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679) función.

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

   Esta función devuelve un `HWND`, que es un identificador a una ventana. Un identificador es en cierto modo como un puntero que Windows usa para realizar un seguimiento de ventanas abiertas. Para obtener más información, consulte [tipos de datos de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383751).

1. En este momento se ha creado la ventana, pero aún necesitamos indicar a Windows para que sea visible. Es lo que hace este código:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   La ventana que se muestra no tiene mucho contenido porque todavía no ha implementado la `WndProc` función. En otras palabras, la aplicación no está controlando todavía los mensajes de Windows ahora está enviando a él.

1. Para controlar los mensajes, primero se agrega un bucle de mensajes para escuchar los mensajes que envía Windows. Cuando la aplicación recibe un mensaje, este bucle lo envía a su `WndProc` función administrará. El bucle de mensajes es similar al código siguiente.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Para obtener más información acerca de las estructuras y funciones en el bucle de mensajes, vea [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958), [GetMessage](https://msdn.microsoft.com/library/windows/desktop/ms644936), [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955), y [DispatchMessage ](https://msdn.microsoft.com/library/windows/desktop/ms644934).

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

   Es un mensaje importante para controlar el [WM_PAINT](https://msdn.microsoft.com/library/windows/desktop/dd145213) mensaje. La aplicación recibe este mensaje cuando debe actualizarse la parte de su ventana mostrada. Este evento puede producirse cuando un usuario mueve una ventana delante de la ventana, a continuación, mueve fuera nuevo. La aplicación no sabe cuando se producen eventos similar al siguiente; Windows sólo conoce, por lo que le avisa con `WM_PAINT`. Cuando se muestra la ventana por primera vez, toda ella debe actualizarse.

   Para controlar un `WM_PAINT` de mensajes, primera llamada [BeginPaint](https://msdn.microsoft.com/library/windows/desktop/dd183362), a continuación, controle toda la lógica para mostrar el texto, botones y otros controles en la ventana y, a continuación, llame a [EndPaint](https://msdn.microsoft.com/library/windows/desktop/dd162598). Para esta aplicación, la lógica entre la llamada inicial y la llamada final consiste en mostrar la cadena "Hola, el escritorio de Windows." en la ventana. En el siguiente código, observe que la [TextOut](https://msdn.microsoft.com/library/windows/desktop/dd145133) función se utiliza para mostrar la cadena.

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

   `HDC`en este código es un identificador de un contexto de dispositivo, que es una estructura de datos que Windows usa para habilitar la aplicación para comunicarse con el subsistema de gráficos. El `BeginPaint` y `EndPaint` funciones Asegúrese de que la aplicación se comporta como un buen ciudadano y no usa el contexto de dispositivo durante más tiempo de lo necesario. Esto ayuda a asegurarse de que el subsistema de gráficos está disponible para su uso por otras aplicaciones.

1. Una aplicación normalmente controla muchos otros mensajes, por ejemplo, [WM_CREATE](https://msdn.microsoft.com/library/windows/desktop/ms632619) cuando se crea una ventana por primera vez, y [WM_DESTROY](https://msdn.microsoft.com/library/windows/desktop/ms632620) cuando se cierra la ventana. El código siguiente muestra una función `WndProc` básica pero completa.

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

Según lo previsto, este es el código completo de la aplicación en funcionamiento.

### <a name="to-build-this-example"></a>Para compilar este ejemplo

1. Eliminar cualquier HelloWindowsDesktop.cpp que ha especificado en el editor de código. Copie este código de ejemplo y, a continuación, péguelo en HelloWindowsDesktop.cpp:

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

1. Para ejecutar la aplicación, presione **F5**. Una ventana que contiene el texto "Hola, el escritorio de Windows." debe aparecer en la esquina superior izquierda de la pantalla.

   ![Ejecute el proyecto DesktopApp](../build/media/desktop-app-project-run-150.gif "ejecutar el proyecto DesktopApp")

¡Enhorabuena! Ha completado este tutorial y compila una aplicación de escritorio tradicional de Windows.

## <a name="see-also"></a>Vea también

[Aplicaciones de escritorio de Windows](../windows/windows-desktop-applications-cpp.md)
