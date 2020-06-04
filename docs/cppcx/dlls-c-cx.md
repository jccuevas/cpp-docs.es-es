---
title: DLL (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 4db0ed4f11f03c65c440c7b654653347da1d4536
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740270"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Puede usar Visual Studio para crear un archivo DLL de Win32 estándar o un archivo DLL de Windows Runtime componente que puedan usar las aplicaciones Plataforma universal de Windows (UWP). Es posible que un archivo DLL estándar que se haya creado con una versión de Visual C++ Studio o el compilador de Microsoft anterior a visual Studio 2012 no se cargue correctamente en una aplicación UWP y que no pase la prueba de comprobación de la aplicación en el Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Archivos dll de Windows Runtime componentes

En casi todos los casos, si desea crear un archivo DLL para usarlo en una aplicación de UWP, créelo como un componente de Windows Runtime mediante el uso de la plantilla de proyecto de ese nombre. Puede crear un proyecto de componente de Windows Runtime para archivos DLL que tengan tipos de Windows Runtime públicos o privados. Se puede tener acceso a un componente de Windows Runtime desde aplicaciones escritas en cualquier lenguaje compatible con Windows Runtime. De forma predeterminada, la configuración del compilador para un proyecto de componente de Windows Runtime usa el modificador **/ZW** Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.

Para obtener más información, consulta [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Para hacer referencia a un archivo binario de un componente de Windows Runtime de terceros en el proyecto

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes** , elige el botón **Agregar nueva referencia** .

1. Un componente de Windows Runtime consta de un archivo DLL y un archivo. winmd que contiene los metadatos. Normalmente, estos archivos se encuentran en la misma carpeta. En el panel izquierdo del cuadro de diálogo **Agregar referencia** , elige el botón **Examinar** y después navega hasta la ubicación del archivo DLL y su archivo .winmd. Para obtener más información, vea [SDK de extensión](/visualstudio/extensibility/creating-a-software-development-kit#extension-sdks).

## <a name="standard-dlls"></a>Archivos DLL estándar

Puede crear un archivo DLL estándar para C++ el código que no consuma ni genere tipos de Windows Runtime públicos y lo consuma desde una aplicación de UWP. Use el tipo de proyecto de biblioteca de vínculos dinámicos (DLL) si solo desea migrar una DLL existente para compilar en esta versión de Visual Studio, pero no convertir el código en un proyecto de componente de Windows Runtime. Al utilizar los pasos siguientes, la DLL se implementará en paralelo con el ejecutable de la aplicación en el paquete .appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Para crear un archivo DLL estándar en Visual Studio

1. En la barra de menús, elija **archivo**, **nuevo**, **proyecto**y, a continuación, seleccione la plantilla **biblioteca de vínculos dinámicos (dll)** .

1. Escribe un nombre para el proyecto y, a continuación, haz clic en el botón **Aceptar** .

1. Agrega el código. Asegúrate de utilizar `__declspec(dllexport)` para las funciones que deseas exportar, por ejemplo, `__declspec(dllexport) Add(int I, in j);`.

1. Agregue `#include winapifamily.h` para incluir ese archivo de encabezado del Windows SDK para las aplicaciones para UWP y establecer `WINAPI_FAMILY=WINAPI_PARTITION_APP`la macro.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Para hacer referencia a un proyecto DLL estándar de la misma solución

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes** , elige el botón **Agregar nueva referencia** .

1. En el panel izquierdo, selecciona **Solución**y, a continuación, activa la casilla adecuada en el panel derecho.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.

### <a name="to-reference-a-standard-dll-binary"></a>Para hacer referencia a un binario DLL estándar

1. Copia el archivo DLL, el archivo .lib y el archivo de encabezado y pégalos en una ubicación conocida, por ejemplo, en la carpeta del proyecto actual.

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades de configuración**, **Vinculador**, **Entrada** , agrega el archivo .lib como una dependencia.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Para migrar un archivo DLL de Win32 existente para la compatibilidad de aplicaciones para UWP

1. Cree un proyecto del tipo DLL (Windows universal) y agréguele el código fuente existente.

1. Agregue `#include winapifamily.h` para incluir ese archivo de encabezado del Windows SDK para las aplicaciones para UWP y establecer `WINAPI_FAMILY=WINAPI_PARTITION_APP`la macro.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.
