---
title: DLL (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 02/06/2018
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16b7ed16ec128f1fbf67d1b62e974ccd7ea5213b
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Puede usar Visual Studio para crear un archivo DLL para Win32 estándar o un DLL que puede utilizarse en aplicaciones de la plataforma Universal de Windows (UWP) del componente en tiempo de ejecución de Windows. Un archivo DLL estándar que se creó con una versión de Visual Studio o el compilador de Visual C++ anterior a la de Visual Studio 2012 puede no cargarse correctamente en una aplicación de UWP y no se puede pasar la prueba de comprobación de la aplicación en Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>DLL de componente en tiempo de ejecución de Windows

En casi todos casos, cuando desea crear un archivo DLL para utilizar en una aplicación UWP, créela como un componente en tiempo de ejecución de Windows mediante la plantilla de proyecto de ese nombre. Puede crear un proyecto de componente en tiempo de ejecución de Windows para archivos DLL que tengan tipos de tiempo de ejecución de Windows públicos o privados. Un componente en tiempo de ejecución de Windows puede tener acceso desde aplicaciones escritas en cualquier lenguaje compatible con Windows en tiempo de ejecución. De forma predeterminada, la configuración de compilador para un componente en tiempo de ejecución de Windows proyectos use la **/ZW** cambiar. Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.

Para obtener más información, consulte [crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Para hacer referencia a un componente de tiempo de ejecución de Windows de terceros binario en el proyecto

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes** , elige el botón **Agregar nueva referencia** .

1. Un componente en tiempo de ejecución de Windows consta de un archivo DLL y un archivo .winmd que contiene los metadatos. Normalmente, estos archivos se encuentran en la misma carpeta. En el panel izquierdo del cuadro de diálogo **Agregar referencia** , elige el botón **Examinar** y después navega hasta la ubicación del archivo DLL y su archivo .winmd. Para obtener más información, consulte [SDK de extensión](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>Archivos DLL estándar

Puede crear un archivo DLL estándar para código de C++ que no consumen o producen tipos públicos de Windows en tiempo de ejecución y usarlo en una aplicación de UWP. Utilice el tipo de proyecto de biblioteca de vínculos dinámicos (DLL) si desea migrar una DLL existente para compilarla en esta versión de Visual Studio pero no quieres convertir el código a un proyecto de componente de Windows en tiempo de ejecución. Al utilizar los pasos siguientes, la DLL se implementará en paralelo con el ejecutable de la aplicación en el paquete .appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Para crear un archivo DLL estándar en Visual Studio

1. En la barra de menús, elija **archivo**, **New**, **proyecto**y, a continuación, seleccione la **biblioteca de vínculos dinámicos (DLL)** plantilla.

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

1. Cree un proyecto del tipo DLL (Windows Universal) y agregue el código fuente existente a él.

1. Agregar `#include winapifamily.h` para incluir el archivo de encabezado de Windows SDK para aplicaciones UWP y establecer la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.
