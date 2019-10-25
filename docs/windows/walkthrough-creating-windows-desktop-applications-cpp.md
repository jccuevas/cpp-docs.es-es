---
title: 'Tutorial: crear una aplicación de escritorio de WindowsC++tradicional ()'
ms.custom: get-started-article
ms.date: 10/21/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: 080c4cd9612058a0a54f19e5d0f4b8add4a03bce
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778549"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Tutorial: crear una aplicación de escritorio de WindowsC++tradicional ()

En este tutorial se muestra cómo crear una aplicación de escritorio de Windows tradicional en Visual Studio. La aplicación de ejemplo que creará usa la API de Windows para mostrar "Hello, escritorio de Windows" en una ventana. Puede utilizar el código que va a desarrollar en este tutorial como modelo para crear otras aplicaciones de escritorio de Windows.

La API de Windows (también conocida como la API de Win32, la API del escritorio de Windows y Windows Classic API) es un marco basado en lenguaje C para crear aplicaciones de Windows. Ha estado existiendo desde el ochenta y se ha usado para crear aplicaciones de Windows durante décadas. Los marcos de trabajo más avanzados y más fáciles de programar se han creado sobre la API de Windows. Por ejemplo, MFC, ATL, .NET Framework. Incluso el código Windows Runtime más moderno para UWP y las aplicaciones de la C++tienda escritas en/WinRT usa la API de Windows que se encuentra debajo. Para obtener más información acerca de la API de Windows, consulte índice de la [API de Windows](/windows/win32/apiindex/windows-api-list). Hay muchas maneras de crear aplicaciones de Windows, pero el proceso anterior fue el primero.

> [!IMPORTANT]
> Por motivos de brevedad, algunas instrucciones de código se omiten en el texto. La sección [compilar el código](#build-the-code) al final de este documento muestra el código completo.

## <a name="prerequisites"></a>Requisitos previos

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Recomendamos Windows 10 para obtener la mejor experiencia de desarrollo.

- Una copia de Visual Studio. Para obtener información sobre cómo descargar e instalar Visual Studio, consulte [Instalación de Visual Studio](/visualstudio/install/install-visual-studio). Al ejecutar el programa de instalación, asegúrese de que la carga de trabaja **Desarrollo para el escritorio con C++** está activada. No se preocupe si no ha instalado esta carga de trabajo al instalar Visual Studio. Puede ejecutar de nuevo el programa de instalación e instalarla ahora.

   ![Desarrollo para el escritorio con C++](../build/media/desktop-development-with-cpp.png "Desarrollo para el escritorio con C++")

- Comprensión de los aspectos básicos del uso de IDE de Visual Studio. Si ha usado antes las aplicaciones de escritorio de Windows, probablemente esté al día. Para ver una introducción, consulte [Paseo por las características del IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Conocer todos los fundamentos del lenguaje C++ para poder continuar. No se preocupe, no hacemos nada que sea muy complicado.

## <a name="create-a-windows-desktop-project"></a>Crear un proyecto de escritorio de Windows

Siga estos pasos para crear su primer proyecto de escritorio de Windows. A medida que avance, escribirá el código para una aplicación de escritorio de Windows operativa. Hay un selector de versión en la parte superior izquierda de esta página. Asegúrese de que está establecido en la versión de Visual Studio que está usando.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Para crear un proyecto de escritorio de Windows en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo , establezca **C++** Language en, establezca **plataforma** en **Windows**y establezca **tipo de proyecto** en **escritorio**.

1. En la lista filtrada de tipos de proyecto, elija **Asistente para escritorio de Windows** y, a continuación, elija **siguiente**. En la página siguiente, escriba un nombre para el proyecto, por ejemplo, *DesktopApp*.

1. Elija el botón **Crear** para crear el proyecto.

1. Aparecerá el cuadro de diálogo **proyecto de escritorio de Windows** . En **tipo de aplicación**, seleccione **aplicación de escritorio (. exe)** . En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Aceptar** para crear el proyecto.

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **DesktopApp** , elija **Agregar**y, a continuación, elija **nuevo elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)** . En el cuadro **nombre** , escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop. cpp*. Haga clic en **Agregar**.

   ![Agregar el archivo. cpp al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Agregar el archivo. cpp al proyecto DesktopApp")

El proyecto se ha creado y el archivo de código fuente se abre en el editor. Para continuar, vaya directamente a [crear el código](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Para crear un proyecto de escritorio de Windows en Visual Studio 2017

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el cuadro de diálogo **nuevo proyecto** , en el panel izquierdo, expanda **instalado** > **C++visual**y, a continuación, seleccione **escritorio de Windows**. En el panel central, seleccione **Asistente para escritorio de Windows**.

   En el cuadro **nombre** , escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Aceptar**.

   ![Asignar un nombre al proyecto DesktopApp](../build/media/desktop-app-new-project-name-153.png "Asignar un nombre al proyecto DesktopApp")

1. En el cuadro de diálogo **proyecto de escritorio de Windows** , en tipo de **aplicación**, seleccione **aplicación para Windows (. exe)** . En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Aceptar** para crear el proyecto.

   ![Crear DesktopApp en el Asistente para proyectos de escritorio de Windows](../build/media/desktop-app-new-project-wizard-153.png "Crear DesktopApp en el Asistente para proyectos de escritorio de Windows")

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **DesktopApp** , elija **Agregar**y, a continuación, elija **nuevo elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)** . En el cuadro **nombre** , escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop. cpp*. Haga clic en **Agregar**.

   ![Agregar el archivo. cpp al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Agregar el archivo. cpp al proyecto DesktopApp")

El proyecto se ha creado y el archivo de código fuente se abre en el editor. Para continuar, vaya directamente a [crear el código](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Para crear un proyecto de escritorio de Windows en Visual Studio 2015

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el cuadro de diálogo **nuevo proyecto** , en el panel izquierdo, expanda **instalado**  > **plantillas**  > **Visual C++** y, a continuación, seleccione **Win32**. En el panel central, seleccione **Proyecto Win32**.

   En el cuadro **nombre** , escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Aceptar**.

   ![Asignar un nombre al proyecto DesktopApp](../build/media/desktop-app-new-project-name-150.png "Asignar un nombre al proyecto DesktopApp")

1. En la página **información general** del **Asistente para aplicaciones Win32**, elija **siguiente**.

   ![Información general del Asistente para crear DesktopApp en la aplicación Win32](../build/media/desktop-app-win32-wizard-overview-150.png "Información general del Asistente para crear DesktopApp en la aplicación Win32")

1. En la página Configuración de la **aplicación** , en **tipo de aplicación**, seleccione aplicación para **Windows**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Finalizar** para crear el proyecto.

   ![Crear DesktopApp en la configuración del Asistente para aplicaciones Win32](../build/media/desktop-app-win32-wizard-settings-150.png "Crear DesktopApp en la configuración del Asistente para aplicaciones Win32")

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto DesktopApp, elija **Agregar**y, a continuación, elija **nuevo elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)** . En el cuadro **nombre** , escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop. cpp*. Haga clic en **Agregar**.

   ![Agregar el archivo. cpp al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Agregar el archivo. cpp al proyecto DesktopApp")

El proyecto se ha creado y el archivo de código fuente se abre en el editor.

::: moniker-end

## <a name="create-the-code"></a>Crear el código

A continuación, aprenderá a crear el código para una aplicación de escritorio de Windows en Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Para iniciar una aplicación de escritorio de Windows

1. Al igual que todas las aplicaciones C++ y aplicaciones de C deben tener una función de `main` como punto de partida, todas las aplicaciones de escritorio de Windows deben tener una función de `WinMain`. `WinMain` tiene la siguiente sintaxis.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Para obtener información sobre los parámetros y el valor devuelto de esta función, vea [WinMain Entry Point](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > ¿Cuáles son todas esas palabras extra, como `CALLBACK`, o `HINSTANCE` o `_In_`? La API tradicional de Windows usa las definiciones de tipos y las macros de preprocesador para abstraer algunos de los detalles de los tipos y el código específico de la plataforma, como convenciones de llamada, declaraciones **_ _ declspec** y pragmas del compilador. En Visual Studio, puede usar la característica de [información rápida](/visualstudio/ide/using-intellisense#quick-info) de IntelliSense para ver lo que definen estas definiciones de tipo y macros. Mantenga el mouse sobre la palabra de interés o selecciónela y presione **ctrl** +**K**, **Ctrl** +**I** para obtener una pequeña ventana emergente que contiene la definición. Para obtener más información, vea [Usar IntelliSense](/visualstudio/ide/using-intellisense). Los parámetros y los tipos devueltos a menudo usan *anotaciones sal* para ayudarle a detectar errores de programación. Para obtener más información, consulte [uso de anotaciones sal para reducir defectosC++ de código C/](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Los programas de escritorio de Windows requieren el > &lt;windows. h. &lt;tchar. h > define la macro `TCHAR`, que se resuelve en última instancia en **wchar_t** si el símbolo Unicode está definido en el proyecto; en caso contrario, se resuelve como **Char**.  Si siempre compila con Unicode habilitado, no necesita TCHAR y solo puede usar **wchar_t** directamente.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Junto con la función `WinMain`, todas las aplicaciones de escritorio de Windows también deben tener una función de procedimiento de ventana. Esta función se denomina normalmente `WndProc`, pero puede asignarle el nombre que desee. `WndProc` tiene la siguiente sintaxis.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   En esta función, se escribe código para controlar *los mensajes* que la aplicación recibe de Windows cuando se producen *eventos* . Por ejemplo, si un usuario elige un botón Aceptar en la aplicación, Windows le enviará un mensaje y podrá escribir código dentro de la función `WndProc` que haga todo lo que sea apropiado. Se denomina *control* de un evento. Solo se administran los eventos que son relevantes para la aplicación.

   Para más información, vea [Procedimientos de ventanas](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Para agregar funcionalidad a la función WinMain

1. En la función `WinMain`, rellenará una estructura de tipo [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). La estructura contiene información sobre la ventana: el icono de la aplicación, el color de fondo de la ventana, el nombre que se va a mostrar en la barra de título, entre otras cosas. Lo importante es que contenga un puntero de función al procedimiento de ventana. El ejemplo siguiente muestra una estructura típica de `WNDCLASSEX` .

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

   Para obtener información sobre los campos de la estructura anterior, vea [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Registre el `WNDCLASSEX` con Windows para que sepa su ventana y cómo enviarle mensajes. Use la función [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) y pase la estructura de clase de ventana como argumento. Se usa la macro `_T` porque usamos el tipo de `TCHAR`.

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

1. Ahora puede crear una ventana. Use la función [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) .

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

   Esta función devuelve un `HWND`, que es un identificador de una ventana. Un identificador es similar a un puntero que Windows usa para realizar un seguimiento de las ventanas abiertas. Para obtener más información, vea [Tipos de datos de Windows](/windows/win32/WinProg/windows-data-types).

1. En este punto, se ha creado la ventana, pero todavía es necesario indicar a Windows que la haga visible. Eso es lo que hace este código:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   La ventana mostrada no tiene mucho contenido porque todavía no ha implementado la función `WndProc`. En otras palabras, la aplicación todavía no controla los mensajes que Windows envía a él.

1. Para controlar los mensajes, primero se agrega un bucle de mensajes para escuchar los mensajes que envía Windows. Cuando la aplicación recibe un mensaje, este bucle lo envía a la función `WndProc` que se va a controlar. El bucle de mensajes es similar al código siguiente.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Para más información sobre las estructuras y funciones que se usan en el bucle de mensajes, vea [MSG](/windows/win32/api/winuser/ns-winuser-msg), [GetMessage](/windows/win32/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

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

   Un mensaje importante para controlar es el mensaje [WM_PAINT](/windows/win32/gdi/wm-paint) . La aplicación recibe el mensaje de `WM_PAINT` cuando se debe actualizar la parte de su ventana mostrada. El evento puede producirse cuando un usuario mueve una ventana delante de la ventana y, a continuación, la mueve de nuevo. La aplicación no sabe cuándo se producen estos eventos. Solo Windows sabe, por lo que notifica a la aplicación un mensaje de `WM_PAINT`. Cuando se muestra la ventana por primera vez, se debe actualizar todo.

   Para controlar un mensaje `WM_PAINT` , primero llame a [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint), controle toda la lógica para mostrar el texto, los botones y otros controles de la ventana y luego llame a [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). Para la aplicación, la lógica entre la llamada inicial y la llamada final consiste en Mostrar la cadena "Hello, escritorio de Windows!" en la ventana. En el siguiente código, observe que la función [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) se usa para mostrar la cadena.

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

   `HDC` en el código es un identificador de un contexto de dispositivo, que es una estructura de datos que Windows usa para permitir que la aplicación se comunique con el subsistema de gráficos. Las funciones `BeginPaint` y `EndPaint` hacen que la aplicación se comporte como un buen ciudadano y no usa el contexto del dispositivo durante más tiempo del necesario. Las funciones ayudan a que el subsistema de gráficos esté disponible para que lo usen otras aplicaciones.

1. Una aplicación normalmente controla muchos otros mensajes. Por ejemplo, [WM_CREATE](/windows/win32/winmsg/wm-create) cuando se crea una ventana por primera vez y [WM_DESTROY](/windows/win32/winmsg/wm-destroy) cuando se cierra la ventana. El código siguiente muestra una función `WndProc` básica pero completa.

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

## <a name="build-the-code"></a>Compilación del código

Como se prometió, este es el código completo de la aplicación de trabajo.

### <a name="to-build-this-example"></a>Para compilar este ejemplo

1. Elimine cualquier código que haya escrito en *HelloWindowsDesktop. cpp* en el editor. Copie este código de ejemplo y péguelo en *HelloWindowsDesktop. cpp*:

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
      _In_opt_ HINSTANCE hPrevInstance,
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

1. En el menú **Compilar** , elija **Compilar solución**. Los resultados de la compilación deben aparecer en la ventana de **salida** de Visual Studio.

   ![Compilar el proyecto DesktopApp](../build/media/desktop-app-project-build-150.gif "Compilar el proyecto DesktopApp")

1. Presione **F5**para ejecutar la aplicación. Una ventana que contiene el texto "Hello, escritorio de Windows!" debe aparecer en la esquina superior izquierda de la pantalla.

   ![Ejecutar el proyecto DesktopApp](../build/media/desktop-app-project-run-157.PNG "Ejecutar el proyecto DesktopApp")

¡Enhorabuena! Ha completado este tutorial y ha creado una aplicación de escritorio de Windows tradicional.

## <a name="see-also"></a>Vea también

[Aplicaciones de escritorio de Windows](../windows/windows-desktop-applications-cpp.md)
