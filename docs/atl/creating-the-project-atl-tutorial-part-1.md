---
title: Crear el proyecto (Tutorial de ATL, Parte 1)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 292faf1769baa2e1c3fc6e52ba6df065cf08766e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221403"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Crear el proyecto (Tutorial de ATL, Parte 1)

Este tutorial le guiará paso a paso a través de un proyecto ATL sin atributos que se crea un objeto ActiveX que muestra un polígono. El objeto incluye opciones para permitir que al usuario para cambiar el número de lados que componen el polígono y el código para actualizar la presentación.

> [!NOTE]
> ATL y MFC no se admiten con carácter general en las ediciones Express de Visual Studio.

> [!NOTE]
> Este tutorial crea el mismo código de origen como en el ejemplo de polígono. Si desea evitar escribir manualmente el código fuente, puede descargarlo desde el [extracto del ejemplo Polygon](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon). A continuación, puede hacer referencia al código fuente polígono como trabajar con el tutorial, o usarlo para comprobar si hay errores en su propio proyecto.
> Para compilar, abra stdafx.h y reemplace:
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
> with
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
> El compilador se quejará todavía sobre `regsvr32` no salir correctamente, pero aún debe tener DLL del control compilado y disponible para su uso.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Para crear el proyecto ATL inicial mediante el Asistente para proyectos ATL

1. En Visual Studio 2017 y versiones anteriores: **Archivo** > **nueva** > **proyecto**. Abrir el **Visual C++**  pestaña y seleccione **MFC/ATL**. Seleccione **proyecto ATL**.

   En Visual Studio de 2019: Elija **archivo** > **New** > **proyecto**, escriba "atl" en el cuadro de búsqueda y elija **proyecto ATL**.

1. Tipo *polígono* como el nombre del proyecto.

    La ubicación para el código fuente normalmente será \Users\\\<username > \source\repos y una nueva carpeta se creará automáticamente.

1. Haga clic en **Aceptar** y **proyecto ATL** abre el asistente.

1. Haga clic en **configuración de la aplicación** para ver las opciones disponibles.

1. Como va a crear un control y un control debe ser un servidor en proceso, deje el **tipo de aplicación** como un archivo DLL.

1. Deje las demás opciones con sus valores predeterminados y haga clic en **Aceptar**.

El **Asistente para proyectos ATL** creará el proyecto mediante la generación de varios archivos. Puede ver estos archivos en **el Explorador de soluciones** expandiendo el `Polygon` objeto. Los archivos se enumeran a continuación.

|Archivo|Descripción|
|----------|-----------------|
|Polygon.cpp|Contiene la implementación de `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, y `DllUnregisterServer`. También contiene el mapa de objetos, que es una lista de los objetos ATL en el proyecto. Esto está inicialmente en blanco.|
|Polygon.def|Este archivo de definición de módulo proporciona al vinculador con información acerca de las exportaciones requeridas por el archivo DLL.|
|Polygon.idl|El archivo de lenguaje de definición de interfaz, que se describe las interfaces específicas de los objetos.|
|Polygon.rgs|Este script de registro contiene información para registrar la DLL del programa.|
|Polygon.rc|El archivo de recursos, que inicialmente contiene la información de versión y una cadena que contiene el nombre del proyecto.|
|Resource.h|El archivo de encabezado para el archivo de recursos.|
|Polygonps.def|Este archivo de definición de módulo proporciona al vinculador con información acerca de las exportaciones requeridas por el código proxy y código auxiliar que permiten las llamadas entre apartamentos.|
|stdafx.cpp|El archivo que incluirá `#include` los archivos de implementación de ATL.|
|stdafx.h|El archivo que incluirá `#include` los archivos de encabezado ATL.|

1. En **el Explorador de soluciones**, haga clic en el `Polygon` proyecto.

1. En el menú contextual, haga clic en **propiedades**.

1. Haga clic en **vinculador**. Cambiar el **por UserRedirection** opción **Sí**.

1. Haga clic en **Aceptar**.

En el paso siguiente, agregará un control a su proyecto.

[En el paso 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Vea también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
