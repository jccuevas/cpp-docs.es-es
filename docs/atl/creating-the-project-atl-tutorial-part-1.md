---
title: Crear el proyecto (Tutorial de ATL, Parte 1)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: b4c18d83feb6c61b603bb1880960193cf9150f9b
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509400"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Crear el proyecto (Tutorial de ATL, Parte 1)

Este tutorial le guía paso a paso a través de un proyecto ATL sin atributos que crea un objeto ActiveX que muestra un polígono. El objeto incluye opciones para permitir que el usuario cambie el número de lados que componen el polígono y el código para actualizar la presentación.

> [!NOTE]
> En este tutorial se crea el mismo código fuente que el ejemplo Polygon. Si desea evitar escribir el código fuente manualmente, puede descargarlo desde el [Resumen de ejemplo de Polygon](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon). Después, puede hacer referencia al código fuente de polígono mientras trabaja en el tutorial, o usarlo para comprobar si hay errores en su propio proyecto.
> Para compilar, Abra *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores) y reemplace:
>
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
>
> con
>
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
>
> El compilador seguirá queja de `regsvr32` no se cierre correctamente, pero debe tener la DLL del control compilada y disponible para su uso.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Para crear el proyecto ATL inicial mediante el Asistente para proyectos ATL

1. En Visual Studio 2017 y versiones anteriores: **archivo** > **nuevo** **proyecto**de > . Abra la pestaña **Visual C++**  y seleccione **MFC/ATL**. Seleccione **proyecto ATL**.

   En Visual Studio 2019: elija **archivo** > **nuevo** > **proyecto**, escriba "ATL" en el cuadro de búsqueda y elija **proyecto ATL**.

1. Escriba *Polygon* como el nombre del proyecto.

    La ubicación del código fuente normalmente tendrá como valor predeterminado \Users\\\<nombreDeUsuario > \source\repos y se creará automáticamente una nueva carpeta.

1. En Visual Studio 2019, acepte los valores predeterminados y haga clic en **Aceptar**. 
   En Visual Studio 2017, haga clic en **Aceptar** para abrir el Asistente para **proyectos ATL** . Haga clic en configuración de la **aplicación** para ver las opciones disponibles. Dado que este proyecto crea un control y un control debe ser un servidor en proceso, deje el **tipo de aplicación** como un archivo dll. Haga clic en **OK**.

Visual Studio creará el proyecto mediante la generación de varios archivos. Puede ver estos archivos en **Explorador de soluciones** expandiendo el objeto `Polygon`. Los archivos se enumeran a continuación.

::: moniker range="<=vs-2017"

|Archivo|Descripción|
|----------|-----------------|
|Polygon. cpp|Contiene la implementación de `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`y `DllUnregisterServer`. También contiene el mapa de objetos, que es una lista de los objetos ATL del proyecto. Está inicialmente en blanco.|
|Polygon. def|Este archivo de definición de módulo proporciona al enlazador información acerca de las exportaciones que requiere el archivo DLL.|
|Polygon. idl|El archivo de lenguaje de definición de interfaz, que describe las interfaces específicas de los objetos.|
|Polygon. RGS|Este script del registro contiene información para registrar el archivo DLL del programa.|
|Polygon. RC|El archivo de recursos, que inicialmente contiene la información de versión y una cadena que contiene el nombre del proyecto.|
|Resource.h|El archivo de encabezado para el archivo de recursos.|
|Polygonps. def|Este archivo de definición de módulo proporciona al enlazador información sobre las exportaciones requeridas por el proxy y el código auxiliar que admiten llamadas entre apartamentos.|
|stdafx.cpp|Archivo que va a `#include` *stdafx. h*.|
|stdafx.h|Archivo que `#include`rá y precompilará los archivos de encabezado ATL.|

::: moniker-end

::: moniker range=">=vs-2019"

|Archivo|Descripción|
|----------|-----------------|
|Polygon. cpp|Contiene la implementación de `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`y `DllUnregisterServer`. También contiene el mapa de objetos, que es una lista de los objetos ATL del proyecto. Está inicialmente en blanco.|
|Polygon. def|Este archivo de definición de módulo proporciona al enlazador información acerca de las exportaciones que requiere el archivo DLL.|
|Polygon. idl|El archivo de lenguaje de definición de interfaz, que describe las interfaces específicas de los objetos.|
|Polygon. RGS|Este script del registro contiene información para registrar el archivo DLL del programa.|
|Polygon. RC|El archivo de recursos, que inicialmente contiene la información de versión y una cadena que contiene el nombre del proyecto.|
|Resource.h|El archivo de encabezado para el archivo de recursos.|
|Polygonps. def|Este archivo de definición de módulo proporciona al enlazador información sobre las exportaciones requeridas por el proxy y el código auxiliar que admiten llamadas entre apartamentos.|
|PCH. cpp|El archivo que `#include` *PCH. h*.|
|PCH. h|Archivo que `#include`rá y precompilará los archivos de encabezado ATL.|

::: moniker-end

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto `Polygon`.

1. En el menú contextual, haga clic en **propiedades**.

1. Haga clic en **enlazador**. Cambie la opción **por UserRedirection** a **sí**.

1. Haga clic en **OK**.

En el paso siguiente, agregará un control al proyecto.

[En el paso 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Consulte también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
