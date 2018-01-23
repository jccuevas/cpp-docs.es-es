---
title: DLL (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 97d6bf2de580e5975be990115c5eb42fab3c3b2e
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Puede usar Visual Studio para crear un archivo DLL para Win32 estándar o un componente de Windows Runtime DLL que puede utilizarse en aplicaciones de la plataforma Universal de Windows. Un archivo DLL estándar que se creó con una versión de Visual Studio o el compilador de Visual C++ anterior a la de Visual Studio 2012 puede no cargarse correctamente en una aplicación de plataforma Universal de Windows y puede no pasar la prueba de comprobación de la aplicación en el [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)].

## <a name="windows-runtime-component-dlls"></a>DLL de componente en tiempo de ejecución de Windows

En casi todos casos, cuando desea crear un archivo DLL para usarlo en una aplicación de plataforma Universal de Windows, créela como un componente en tiempo de ejecución de Windows mediante la plantilla de proyecto de ese nombre. Puede crear un proyecto de componente en tiempo de ejecución de Windows para archivos DLL que tengan tipos de tiempo de ejecución de Windows públicos o privados. Un componente en tiempo de ejecución de Windows puede tener acceso desde aplicaciones escritas en cualquier lenguaje compatible con Windows en tiempo de ejecución. De forma predeterminada, la configuración de compilador para un componente en tiempo de ejecución de Windows proyectos use la **/ZW** cambiar. Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.

Para obtener más información, consulte [crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Para hacer referencia a un componente de tiempo de ejecución de Windows de terceros binario en el proyecto

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes** , elige el botón **Agregar nueva referencia** .

1. Un componente en tiempo de ejecución de Windows consta de un archivo DLL y un archivo .winmd que contiene los metadatos. Normalmente, estos archivos se encuentran en la misma carpeta. En el panel izquierdo del cuadro de diálogo **Agregar referencia** , elige el botón **Examinar** y después navega hasta la ubicación del archivo DLL y su archivo .winmd. Para obtener más información, consulte [SDK de extensión](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>Archivos DLL estándar

Puede crear un archivo DLL estándar para código de C++ que no consumen o producen tipos públicos de Windows en tiempo de ejecución y usarlo desde una aplicación de plataforma Universal de Windows. Utilice el tipo de proyecto de DLL de plataforma Universal de Windows si desea migrar una DLL existente para compilarla en esta versión de Visual Studio pero no quieres convertir el código a un proyecto de componente de Windows en tiempo de ejecución. Al utilizar los pasos siguientes, la DLL se implementará en paralelo con el ejecutable de la aplicación en el paquete .appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Para crear un archivo DLL estándar en Visual Studio

1. En la barra de menús, elija **archivo**, **New**, **proyecto**y, a continuación, seleccione la plantilla DLL de plataforma Universal de Windows.

1. Escribe un nombre para el proyecto y, a continuación, haz clic en el botón **Aceptar** .

1. Agrega el código. Asegúrate de utilizar `__declspec(dllexport)` para las funciones que deseas exportar, por ejemplo, `__declspec(dllexport) Add(int I, in j);`.

1. Agregar `#include winapifamily.h` para incluir el archivo de encabezado de Windows SDK para aplicaciones de la plataforma Universal de Windows y establecer la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Para hacer referencia a un proyecto DLL estándar de la misma solución

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes** , elige el botón **Agregar nueva referencia** .

1. En el panel izquierdo, selecciona **Solución**y, a continuación, activa la casilla adecuada en el panel derecho.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.

### <a name="to-reference-a-standard-dll-binary"></a>Para hacer referencia a un binario DLL estándar

1. Copia el archivo DLL, el archivo .lib y el archivo de encabezado y pégalos en una ubicación conocida, por ejemplo, en la carpeta del proyecto actual.

1. Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades de configuración**, **Vinculador**, **Entrada** , agrega el archivo .lib como una dependencia.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.

### <a name="to-migrate-an-existing-win32-dll-for-universal-windows-platform-app-compatibility"></a>Para migrar un archivo DLL para Win32 existente para la compatibilidad de aplicaciones de plataforma Universal de Windows

1. Cree un proyecto del tipo de DLL de plataforma Universal de Windows y agregue el código fuente existente a él.

1. Agregar `#include winapifamily.h` para incluir el archivo de encabezado de Windows SDK para aplicaciones de la plataforma Universal de Windows y establecer la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.
