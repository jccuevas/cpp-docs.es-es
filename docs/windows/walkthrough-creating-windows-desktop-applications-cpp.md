---
title: 'Tutorial: Crear una aplicación de escritorio de Windows tradicional (C++)'
description: Cómo crear una aplicación de escritorio de Windows tradicional y mínima con Visual Studio, C++ y la API de Win32
ms.custom: get-started-article
ms.date: 11/03/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: da74778e79a08dd3ed2b5be0675981425264bdc0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351849"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Tutorial: Crear una aplicación de escritorio de Windows tradicional (C++)

En este tutorial se muestra cómo crear una aplicación de escritorio tradicional de Windows en Visual Studio. La aplicación de ejemplo que creará usa la API de Windows para mostrar "Hola, escritorio de Windows!" en una ventana. Puede utilizar el código que va a desarrollar en este tutorial como modelo para crear otras aplicaciones de escritorio de Windows.

La API de Windows (también conocida como la API de Win32, la API de escritorio de Windows y la API clásica de Windows) es un marco basado en lenguaje C para crear aplicaciones de Windows. Ha existido desde la década de 1980 y se ha utilizado para crear aplicaciones de Windows durante décadas. Los marcos más avanzados y fáciles de programar se han creado sobre la API de Windows. Por ejemplo, MFC, ATL, los marcos de .NET. Incluso el código de Windows Runtime más moderno para aplicaciones para UWP y Store escrito en C++/WinRT usa la API de Windows debajo. Para obtener más información acerca de la API de Windows, consulte Índice de API de [Windows](/windows/win32/apiindex/windows-api-list). Hay muchas maneras de crear aplicaciones de Windows, pero el proceso anterior fue el primero.

> [!IMPORTANT]
> En aras de la brevedad, algunas instrucciones de código se omiten en el texto. La sección [Compilar el código](#build-the-code) al final de este documento muestra el código completo.

## <a name="prerequisites"></a>Prerrequisitos

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Recomendamos Windows 10 para obtener la mejor experiencia de desarrollo.

- Una copia de Visual Studio. Para obtener información sobre cómo descargar e instalar Visual Studio, consulte [Instalación de Visual Studio](/visualstudio/install/install-visual-studio). Al ejecutar el programa de instalación, asegúrese de que la carga de trabaja **Desarrollo para el escritorio con C++** está activada. No se preocupe si no ha instalado esta carga de trabajo al instalar Visual Studio. Puede ejecutar de nuevo el programa de instalación e instalarla ahora.

   ![Desarrollo para el escritorio con C++](../build/media/desktop-development-with-cpp.png "Desarrollo para el escritorio con C++")

- Comprensión de los aspectos básicos del uso de IDE de Visual Studio. Si ha usado antes las aplicaciones de escritorio de Windows, probablemente esté al día. Para ver una introducción, consulte [Paseo por las características del IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Conocer todos los fundamentos del lenguaje C++ para poder continuar. No se preocupe, no hacemos nada que sea muy complicado.

## <a name="create-a-windows-desktop-project"></a>Crear un proyecto de escritorio de Windows

Siga estos pasos para crear su primer proyecto de escritorio de Windows. A medida que avanza, introducirá el código de una aplicación de escritorio de Windows en funcionamiento. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Para crear un proyecto de escritorio de Windows en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Idioma** en **C++,** Establezca **Plataforma** en **Windows**y Tipo de **proyecto** en **Escritorio**.

1. En la lista filtrada de tipos de proyecto, elija **Asistente para escritorio** de Windows y, a continuación, elija **Siguiente**. En la página siguiente, escriba un nombre para el proyecto, por ejemplo, *DesktopApp*.

1. Elija el botón **Crear** para crear el proyecto.

1. Ahora aparece el cuadro de diálogo Proyecto de escritorio de **Windows.** En **Tipo de aplicación**, seleccione Aplicación de escritorio **(.exe).** En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Aceptar** para crear el proyecto.

1. En **el Explorador**de soluciones , haga clic con el botón secundario en el proyecto **DesktopApp,** elija **Agregar**y, a continuación, elija Nuevo **elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**. En el cuadro **Nombre,** escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop.cpp*. Elija **Add**.

   ![Agregar archivo .cpp al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Agregar archivo .cpp al proyecto DesktopApp")

El proyecto se ha creado y el archivo de origen se abre en el editor. Para continuar, vaya a [Crear el código](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Para crear un proyecto de escritorio de Windows en Visual Studio 2017

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto,** en el panel izquierdo, expanda**Visual C++** **instalado** > y, a continuación, seleccione **Escritorio de Windows**. En el panel central, seleccione **Asistente para escritorio**de Windows .

   En el cuadro **Nombre,** escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Ok**.

   ![Asigne un nombre al proyecto DesktopApp](../build/media/desktop-app-new-project-name-153.png "Asigne un nombre al proyecto DesktopApp")

1. En el cuadro de diálogo Proyecto de escritorio de **Windows** , en Tipo **de aplicación**, seleccione Aplicación de Windows **(.exe).** En **Opciones adicionales**, seleccione **Proyecto vacío**. Asegúrese de que **El encabezado precompilado** no esté seleccionado. Elija **Aceptar** para crear el proyecto.

1. En **el Explorador**de soluciones , haga clic con el botón secundario en el proyecto **DesktopApp,** elija **Agregar**y, a continuación, elija Nuevo **elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**. En el cuadro **Nombre,** escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop.cpp*. Elija **Add**.

   ![Agregar archivo .cpp al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Agregar archivo .cpp al proyecto DesktopApp")

El proyecto se ha creado y el archivo de origen se abre en el editor. Para continuar, vaya a [Crear el código](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Para crear un proyecto de escritorio de Windows en Visual Studio 2015

1. En el menú **Archivo**, elija **Nuevo** y después **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto,** en el panel izquierdo, expanda**Plantillas** >  **instaladas** > **Visual C++** y, a continuación, seleccione **Win32**. En el panel central, seleccione **Proyecto Win32**.

   En el cuadro **Nombre,** escriba un nombre para el proyecto, por ejemplo, *DesktopApp*. Elija **Ok**.

   ![Asigne un nombre al proyecto DesktopApp](../build/media/desktop-app-new-project-name-150.png "Asigne un nombre al proyecto DesktopApp")

1. En la página **Overview (Información general)** del **Asistente para aplicaciones Win32**, elija **Next (Siguiente).**

   ![Crear DesktopApp en Información general del Asistente para aplicaciones Win32](../build/media/desktop-app-win32-wizard-overview-150.png "Crear DesktopApp en Información general del Asistente para aplicaciones Win32")

1. En la página **Configuración** de la aplicación, en **Tipo de aplicación**, seleccione Aplicación de **Windows**. En **Opciones adicionales**, desactive Encabezado **precompilado**y, a continuación, seleccione **Vaciar proyecto**. Elija **Finalizar** para crear el proyecto.

1. En **el Explorador**de soluciones , haga clic con el botón secundario en el proyecto DesktopApp, elija **Agregar**y, a continuación, elija Nuevo **elemento**.

   ![Agregar nuevo elemento al proyecto DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Agregar nuevo elemento al proyecto DesktopApp")

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo C++ (.cpp)**. En el cuadro **Nombre,** escriba un nombre para el archivo, por ejemplo, *HelloWindowsDesktop.cpp*. Elija **Add**.

   ![Agregar archivo .cpp al proyecto DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Agregar archivo .cpp al proyecto DesktopApp")

El proyecto se ha creado y el archivo de origen se abre en el editor.

::: moniker-end

## <a name="create-the-code"></a>Crear el código

A continuación, aprenderá a crear el código para una aplicación de escritorio de Windows en Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Para iniciar una aplicación de escritorio de Windows

1. Al igual que cada aplicación de C `main` y C+ debe tener una función como punto de partida, cada aplicación de escritorio de Windows debe tener una `WinMain` función. `WinMain` tiene la siguiente sintaxis.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Para obtener información sobre los parámetros y el valor devuelto de esta función, vea Punto de [entrada WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > ¿Cuáles son todas esas `CALLBACK`palabras adicionales, como , o `HINSTANCE`, o `_In_`? La API tradicional de Windows usa typedefs y macros de preprocesador ampliamente para abstraer algunos de los detalles de tipos y código específico de la plataforma, como convenciones de llamada, declaraciones **de __declspec** y pragmas del compilador. En Visual Studio, puede usar la característica [Información rápida](/visualstudio/ide/using-intellisense#quick-info) de IntelliSense para ver lo que definen estas operaciones de tipo y macros. Pase el ratón sobre la palabra de interés o selecciónela y pulse **Ctrl**+**K**, **Ctrl**+**I** para una pequeña ventana emergente que contenga la definición. Para obtener más información, vea [Usar IntelliSense](/visualstudio/ide/using-intellisense). Los parámetros y tipos de valor devuelto suelen utilizar *anotaciones SAL* para ayudarle a detectar errores de programación. Para obtener más información, consulte Uso de [anotaciones SAL para reducir defectos de código C/C++.](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)

1. Los programas &lt;de escritorio de Windows requieren> windows.h. &lt;tchar.h> `TCHAR` define la macro, que se resuelve en última instancia **en wchar_t** si el símbolo UNICODE se define en el proyecto, de lo contrario se resuelve **en char**.  Si siempre compila con UNICODE habilitado, no necesita TCHAR y solo puede usar **wchar_t** directamente.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Junto con `WinMain` la función, cada aplicación de escritorio de Windows también debe tener una función de procedimiento de ventana. Esta función se `WndProc`denomina normalmente , pero puede asignarle el nombre que desee. `WndProc` tiene la siguiente sintaxis.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   En esta función, escribirá código para controlar los *mensajes* que la aplicación recibe de Windows cuando se producen *eventos.* Por ejemplo, si un usuario elige un botón Aceptar en la aplicación, Windows `WndProc` le enviará un mensaje y podrá escribir código dentro de la función que haga el trabajo que sea adecuado. Se llama *manejar* un evento. Solo controla los eventos que son relevantes para la aplicación.

   Para más información, vea [Procedimientos de ventanas](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Para agregar funcionalidad a la función WinMain

1. En `WinMain` la función, se rellena una estructura de tipo [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). La estructura contiene información sobre la ventana: el icono de la aplicación, el color de fondo de la ventana, el nombre que se mostrará en la barra de título, entre otras cosas. Es importante destacar que contiene un puntero de función al procedimiento de ventana. El ejemplo siguiente muestra una estructura típica de `WNDCLASSEX` .

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

   Para obtener información sobre los campos de la estructura anterior, consulte [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Regístrese `WNDCLASSEX` en Windows para que sepa sobre su ventana y cómo enviarle mensajes. Use la función [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) y pase la estructura de clase de ventana como argumento. La `_T` macro se utiliza `TCHAR` porque usamos el tipo.

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

   Esta función `HWND`devuelve un , que es un identificador de una ventana. Un identificador es algo así como un puntero que Windows utiliza para realizar un seguimiento de las ventanas abiertas. Para obtener más información, vea [Tipos de datos de Windows](/windows/win32/WinProg/windows-data-types).

1. En este punto, se ha creado la ventana, pero todavía tenemos que decirle a Windows que la haga visible. Eso es lo que hace este código:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   La ventana mostrada no tiene mucho contenido porque aún no `WndProc` ha implementado la función. En otras palabras, la aplicación aún no está controlando los mensajes que Windows le está enviando ahora.

1. Para controlar los mensajes, primero agregamos un bucle de mensajes para escuchar los mensajes que Windows envía. Cuando la aplicación recibe un mensaje, este `WndProc` bucle lo distribuye a la función que se va a controlar. El bucle de mensajes es similar al código siguiente.

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

   Un mensaje importante a manejar es el [mensaje WM_PAINT.](/windows/win32/gdi/wm-paint) La aplicación recibe `WM_PAINT` el mensaje cuando se debe actualizar parte de su ventana mostrada. El evento puede producirse cuando un usuario mueve una ventana delante de la ventana y, a continuación, la aleja de nuevo. La aplicación no sabe cuándo se producen estos eventos. Solo Windows lo sabe, por lo `WM_PAINT` que notifica a la aplicación con un mensaje. Cuando se muestra la ventana por primera vez, todo debe actualizarse.

   Para controlar un mensaje `WM_PAINT` , primero llame a [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint), controle toda la lógica para mostrar el texto, los botones y otros controles de la ventana y luego llame a [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). Para la aplicación, la lógica entre la llamada inicial y la llamada final es mostrar la cadena "Hello, Windows desktop!" en la ventana. En el siguiente código, observe que la función [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) se usa para mostrar la cadena.

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

   `HDC`en el código es un identificador de un contexto de dispositivo, que es una estructura de datos que Windows utiliza para permitir que la aplicación se comunique con el subsistema de gráficos. Las `BeginPaint` `EndPaint` funciones y las hacen que la aplicación se comporte como un buen ciudadano y no utiliza el contexto del dispositivo durante más tiempo del necesario. Las funciones ayudan a que el subsistema de gráficos esté disponible para su uso por otras aplicaciones.

1. Normalmente, una aplicación controla muchos otros mensajes. Por ejemplo, [WM_CREATE](/windows/win32/winmsg/wm-create) cuando se crea una ventana por primera vez y [WM_DESTROY](/windows/win32/winmsg/wm-destroy) cuando se cierra la ventana. El código siguiente muestra una función `WndProc` básica pero completa.

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

Como se prometió, aquí está el código completo para la aplicación de trabajo.

### <a name="to-build-this-example"></a>Para compilar este ejemplo

1. Elimine cualquier código que haya introducido en *HelloWindowsDesktop.cpp* en el editor. Copie este código de ejemplo y, a continuación, péguelo en *HelloWindowsDesktop.cpp:*

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

1. En el menú **Compilar** , elija **Compilar solución**. Los resultados de la compilación deben aparecer en el **salida** ventana en Visual Studio.

   ![Compile el proyecto DesktopApp](../build/media/desktop-app-project-build-150.gif "Compile el proyecto DesktopApp")

1. Para ejecutar la aplicación, presione **F5**. Una ventana que contiene el texto "Hola, escritorio de Windows!" debe aparecer en la esquina superior izquierda de la pantalla.

   ![Ejecute el proyecto DesktopApp](../build/media/desktop-app-project-run-157.PNG "Ejecute el proyecto DesktopApp")

¡Enhorabuena! Ha completado este tutorial y ha creado una aplicación de escritorio tradicional de Windows.

## <a name="see-also"></a>Consulte también

[Aplicaciones de escritorio de Windows](../windows/windows-desktop-applications-cpp.md)
