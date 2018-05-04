---
title: Crear el proyecto (ATL Tutorial, parte 1) | Documentos de Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aedf7b4112d4c8d4bb5b2a174e93925f5a46ce5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Crear el proyecto (Tutorial de ATL, Parte 1)
Este tutorial le guía paso a paso para un proyecto ATL sin atributos que crea un objeto ActiveX que muestra un polígono. El objeto incluye opciones para permitir que al usuario para cambiar el número de lados que componen el polígono y el código para actualizar la presentación.  
  
> [!NOTE]
>  ATL y MFC no se admiten normalmente en las ediciones Express de Visual Studio.  
  
> [!NOTE]
>  Este tutorial crea el mismo código de origen como en el ejemplo de polígono. Si desea evitar escribir manualmente el código fuente, puede descargarlo desde el [extracto del ejemplo Polygon](../visual-cpp-samples.md). A continuación, puede hacer referencia al código fuente de Polygon a medida que trabajar con el tutorial, o utilizarlo para comprobar si hay errores en su propio proyecto.  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Para crear el proyecto ATL inicial mediante el Asistente para proyectos ATL  
  
1.  En el entorno de desarrollo de Visual Studio, haga clic en **New** en el **archivo** menú y, a continuación, haga clic en **proyecto**.  
  
2.  Haga clic en el **proyectos de Visual C++** carpeta y seleccione **proyecto ATL**.  
  
3.  Tipo `Polygon` como el nombre del proyecto.  
  
     La ubicación para el código fuente normalmente predeterminado será Mis documentos\Visual Studio Projects y automáticamente se creará una nueva carpeta.  
  
4.  Haga clic en **Aceptar** y abre el Asistente para proyectos ATL.  
  
5.  Haga clic en **configuración de la aplicación** para ver las opciones disponibles.  
  
6.  Crea un control y un control debe ser un servidor en proceso, deje el **tipo de aplicación** como un archivo DLL.  
  
7.  Deje las demás opciones en sus valores predeterminados y haga clic en **finalizar**.  
  
 El Asistente para proyectos ATL creará el proyecto generando varios archivos. Puede ver estos archivos en el Explorador de soluciones, expanda el objeto de polígono. Los archivos se enumeran a continuación.  
  
|Archivo|Descripción|  
|----------|-----------------|  
|Polygon.cpp|Contiene la implementación de `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, y `DllUnregisterServer`. También contiene el mapa de objetos, que es una lista de los objetos ATL en el proyecto. Esto está inicialmente en blanco.|  
|Polygon.def|Este archivo de definición de módulo proporciona al vinculador información sobre las exportaciones requeridas por el archivo DLL.|  
|Polygon.idl|El archivo de lenguaje de definición de interfaz, que describe las interfaces específicas de los objetos.|  
|Polygon.rgs|Esta secuencia de comandos del registro contiene información para registrar la DLL del programa.|  
|Polygon.rc|El archivo de recursos, que inicialmente contiene la información de versión y una cadena que contiene el nombre del proyecto.|  
|Resource.h|El archivo de encabezado para el archivo de recursos.|  
|Polygonps.def|Este archivo de definición de módulo proporciona al vinculador información sobre las exportaciones requeridas por el código proxy y código auxiliar que permiten las llamadas entre apartamentos.|  
|stdafx.cpp|El archivo que incluirá `#include` los archivos de implementación ATL.|  
|stdafx.h|El archivo que incluirá `#include` los archivos de encabezado ATL.|  
  
1.  En el Explorador de soluciones, haga clic en el `Polygon` proyecto.  
  
2.  En el menú contextual, haga clic en **propiedades**.  
  
3.  Haga clic en **vinculador**. Cambiar el **por UserRedirection** opción **Sí**.  
  
4.  Haga clic en **Aceptar**.  
  
 En el paso siguiente, agregará un control al proyecto.  
  
 [En el paso 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

