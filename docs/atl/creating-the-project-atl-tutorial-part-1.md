---
title: "Crear el proyecto (Tutorial de ATL, Parte 1) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Crear el proyecto (Tutorial de ATL, Parte 1)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tutorial recorre paso a paso un proyecto sin atributos ATL que cree un objeto ActiveX que muestra un polígono.  El objeto incluye opciones para permitir que el usuario cambie el número de lados que componen el polígono, y el código para actualizar la presentación.  
  
> [!NOTE]
>  ATL y MFC no se admiten normalmente en las ediciones Express de Visual Studio.  
  
> [!NOTE]
>  Este tutorial crea el mismo código fuente que el ejemplo Polygon.  Si desea evitar escribir código fuente manualmente, puede descargarlo de [Resumen del polígono](../top/visual-cpp-samples.md).  Puede hacer referencia al código fuente Polygon al realizar el tutorial, o lo utiliza para comprobar errores en dispone de proyecto.  
  
### Para crear el proyecto inicial ATL mediante el asistente para proyectos ATL  
  
1.  En el entorno de desarrollo de Visual Studio, haga clic **Nueva** en el menú **Archivo**, y haga clic en **proyecto**.  
  
2.  Haga clic en la carpeta **Proyectos de Visual C** y seleccione **Proyecto ATL**.  
  
3.  Tipo `Polígono` como nombre del proyecto.  
  
     La ubicación del código fuente establecerá como valor predeterminado normalmente a mis documentos \\visual \\Visual Studio Projects \\Visual Studio Projects, y una nueva carpeta se creará automáticamente.  
  
4.  Haga clic **Aceptar** y el asistente para proyectos ATL.  
  
5.  Haga clic **Configuración de la aplicación** para ver las opciones disponibles.  
  
6.  Mientras está creando un control, un control debe ser un servidor en proceso, permite **Tipo de aplicación** como DLL.  
  
7.  Deje las otras opciones en sus valores predeterminados, y haga clic **finalizar**.  
  
 El asistente para proyectos ATL creará el proyecto genera varios archivos.  Puede ver estos archivos en el explorador de soluciones expandiendo el objeto Polygon.  Los archivos se enumeran.  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|Polygon.cpp|Contiene la implementación de `DllMain`, de `DllCanUnloadNow`, de `DllGetClassObject`, de `DllRegisterServer`, y de `DllUnregisterServer`.  También contiene el mapa de objetos, que es una lista de objetos ATL en el proyecto.  Esto es inicialmente en blanco.|  
|Polygon.def|Este archivo de la módulo\- definición proporciona el vinculador con información sobre exportaciones requeridas por el archivo DLL.|  
|Polygon.idl|El archivo de lenguaje de definición de interfaz, que describe las interfaces específicas de los objetos.|  
|Polygon.rgs|Este script de registro contiene información para registrar la DLL del programa.|  
|Polygon.rc|El archivo de recursos, que inicialmente contiene la información de versión y una cadena que contenga el nombre del proyecto.|  
|Resource.h|Archivo de encabezado del archivo de recursos.|  
|Polygonps.def|Este archivo de definición de módulo proporciona el vinculador con información sobre exportaciones que requiere el proxy y código auxiliar que las llamadas admiten entre apartamentos.|  
|stdafx.cpp|El archivo que `#include` implementar archivos de ATL.|  
|stdafx.h|El archivo que `#include` los archivos de encabezado ATL.|  
  
1.  En el explorador de soluciones, haga clic con el botón secundario en el proyecto de `Polygon`.  
  
2.  En el menú contextual, haga clic en **propiedades**.  
  
3.  Haga clic en **Vinculador**.  Cambie la opción **Por\-usuarioRedirección** a **Sí**.  
  
4.  Haga clic en **Aceptar**.  
  
 En el paso siguiente, agregará un control al proyecto.  
  
 [En el paso 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)