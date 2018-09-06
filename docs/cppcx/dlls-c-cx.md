---
title: DLL (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 02/06/2018
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac06336e5ba80406157285ebe660080aff6e319
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763638"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Puede usar Visual Studio para crear un archivo DLL para Win32 estándar o un componente en tiempo de ejecución de Windows del archivo DLL que puede utilizarse en aplicaciones de plataforma Universal de Windows (UWP). Un archivo DLL estándar que se creó con una versión de Visual Studio o el compilador de Visual C++ anterior a la de Visual Studio 2012 puede no cargarse correctamente en una aplicación para UWP y puede no pasar la prueba de comprobación de la aplicación en la Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Archivos DLL de componente en tiempo de ejecución de Windows

En casi todos los casos, cuando desea crear un archivo DLL para usar en una aplicación UWP, créela como un componente en tiempo de ejecución de Windows mediante el uso de la plantilla de proyecto de ese nombre. Puede crear un proyecto de componente en tiempo de ejecución de Windows para archivos DLL que tienen tipos en tiempo de ejecución de Windows públicos o privados. Un componente de Windows Runtime se puede acceder desde las aplicaciones escritas en cualquier lenguaje compatible con Windows en tiempo de ejecución. De forma predeterminada, la configuración del compilador para un componente de Windows en tiempo de ejecución del proyecto utilice el **/ZW** cambie. Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.

Para obtener más información, consulte [crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Para hacer referencia a un componente de Windows en tiempo de ejecución de terceros binario en el proyecto

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes** , elige el botón **Agregar nueva referencia** .

1. Un componente en tiempo de ejecución de Windows consta de un archivo DLL y un archivo .winmd que contiene los metadatos. Normalmente, estos archivos se encuentran en la misma carpeta. En el panel izquierdo del cuadro de diálogo **Agregar referencia** , elige el botón **Examinar** y después navega hasta la ubicación del archivo DLL y su archivo .winmd. Para obtener más información, consulte [SDK de extensión](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>Archivos DLL estándar

Puede crear un archivo DLL estándar para código C++ que no consumen o generan tipos públicos de Windows en tiempo de ejecución y consumirlo desde una aplicación para UWP. Utilice el tipo de proyecto de biblioteca de vínculos dinámicos (DLL) cuando desee migrar una DLL existente para compilarla en esta versión de Visual Studio, pero no convertir el código en un proyecto de componente de Windows en tiempo de ejecución. Al utilizar los pasos siguientes, la DLL se implementará en paralelo con el ejecutable de la aplicación en el paquete .appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Para crear un archivo DLL estándar en Visual Studio

1. En la barra de menús, elija **archivo**, **New**, **proyecto**y, a continuación, seleccione el **biblioteca de vínculos dinámicos (DLL)** plantilla.

1. Escribe un nombre para el proyecto y, a continuación, haz clic en el botón **Aceptar** .

1. Agrega el código. Asegúrate de utilizar `__declspec(dllexport)` para las funciones que deseas exportar, por ejemplo, `__declspec(dllexport) Add(int I, in j);`.

1. Agregar `#include winapifamily.h` para incluir el archivo de encabezado de Windows SDK para aplicaciones UWP y establecer la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Para hacer referencia a un proyecto DLL estándar de la misma solución

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes** , elige el botón **Agregar nueva referencia** .

1. En el panel izquierdo, selecciona **Solución**y, a continuación, activa la casilla adecuada en el panel derecho.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.

### <a name="to-reference-a-standard-dll-binary"></a>Para hacer referencia a un binario DLL estándar

1. Copia el archivo DLL, el archivo .lib y el archivo de encabezado y pégalos en una ubicación conocida, por ejemplo, en la carpeta del proyecto actual.

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades de configuración**, **Vinculador**, **Entrada** , agrega el archivo .lib como una dependencia.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Para migrar un archivo DLL para Win32 existente para la compatibilidad de aplicaciones UWP

1. Cree un proyecto del tipo DLL (Windows Universal) y agregue el código fuente existente a ella.

1. Agregar `#include winapifamily.h` para incluir el archivo de encabezado de Windows SDK para aplicaciones UWP y establecer la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.
