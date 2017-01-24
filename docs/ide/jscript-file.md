---
title: "Archivo JScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddConfig (método)"
  - "AddFilesToCustomProj (método)"
  - "AddFilters (método)"
  - "Common.js (archivo)"
  - "CreateCustomInfFile (método)"
  - "CreateCustomProject (método)"
  - "asistentes personalizados, acceso al modelo de objetos para asistentes"
  - "asistentes personalizados, archivo JScript"
  - "depurar [JScript], habilitar la depuración de secuencias de comandos"
  - "depurar [JScript], JScript (archivos)"
  - "depurar secuencias de comandos"
  - "depurar secuencias de comandos, habilitar la depuración de secuencias de comandos"
  - "Default.js (archivo)"
  - "DelFile (método)"
  - "archivos [C++], creado mediante un asistente personalizado"
  - "GetTargetName (método)"
  - "JScript (archivos)"
  - "OnFinish (método)"
  - "PchSettings (método)"
ms.assetid: 7841a09e-2dd2-4f1a-a13a-39ac53f24315
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivo JScript
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El [Asistente personalizado](../ide/custom-wizard.md) obtiene acceso al motor de script y crea un archivo JScript, denominado Default.js, para cada proyecto.  Asimismo, incluye un archivo [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md).  Estos archivos contienen funciones de JScript que proporcionan acceso a los modelos de objetos de Visual Studio y de Visual C\+\+ para personalizar un asistente.  Vea [Diseñar un asistente](../ide/designing-a-wizard.md) para obtener una lista de estos modelos. Podrá agregar sus propias funciones en el archivo Default.js del proyecto de asistente.  Para obtener acceso a las propiedades y métodos del modelo de objetos del asistente o del modelo de objetos del entorno a partir de un archivo JScript, anteponga "wizard." o "dte.", respectivamente, al elemento correspondiente del modelo de objetos.  
  
 Por ejemplo:  
  
```  
function CreateCustomProject(strProjectName, strProjectPath)  
{  
   try  
   {  
      var strProjTemplatePath = wizard.FindSymbol('PROJECT_TEMPLATE_PATH');  
var strProjTemplate = '';  
      strProjTemplate = strProjTemplatePath + '\\default.vcproj';  
  
      var Solution = dte.Solution;  
      var strSolutionName = "";  
      if (wizard.FindSymbol("CLOSE_SOLUTION"))  
...  
```  
  
 Al hacer clic en **Finalizar** en el [Asistente personalizado](../ide/custom-wizard.md), el asistente carga el archivo Default.js en la carpeta Archivos de script del Explorador de soluciones.  Este archivo JScript crea proyectos, representa plantillas y, a continuación, las agrega a la solución cuando el usuario hace clic en el botón **Finalizar** del asistente.  
  
 De forma predeterminada, el archivo Default.js del proyecto incluye las siguientes funciones:  
  
|Nombre de la función|Descripción|  
|--------------------------|-----------------|  
|**AddConfig**|Agrega las configuraciones del proyecto.  Se pueden suministrar configuraciones propias para el compilador y el vinculador.|  
|**AddFilesToCustomProj**|Cuando el usuario hace clic en **Finalizar**, agrega los archivos especificados al proyecto.|  
|**AddFilters**|Cuando el usuario hace clic en **Finalizar**, agrega los filtros de origen especificados al proyecto.|  
|**CreateCustomProject**|Cuando el usuario hace clic en **Finalizar**, crea el proyecto en la ubicación especificada.|  
|**CreateCustomInfFile**|Crea el [archivo Templates.inf](../ide/templates-inf-file.md) del proyecto.|  
|**DelFile**|Elimina el archivo especificado.|  
|**GetTargetName**|Obtiene el nombre del archivo especificado.|  
|**OnFinish**|El asistente llama a esta función cuando el usuario hace clic en **Finalizar** para crear el proyecto, agregar archivos y filtros, representar plantillas y establecer la configuración.|  
|**PchSettings**|Establece la configuración del encabezado precompilado.  Vea [SetCommonPchSettings](../ide/setcommonpchsettings.md) en la referencia del archivo Common.js para obtener más información.|  
  
 Cada asistente tiene un único archivo Default.js en el que se incluyen los comentarios TODO que ayudan a identificar dónde se debe personalizar el archivo.  
  
 Visual C\+\+ también crea [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md), archivo compartido por todos los asistentes e incluido en el proyecto del asistente.  Las funciones de Common.js pueden utilizarse libremente.  
  
> [!NOTE]
>  Common.js contiene descripciones de cada función y de sus parámetros.  Vea los comentarios del archivo Common.js para obtener más información.  
  
 Si desea compartir determinadas funciones entre sus proyectos de asistentes, puede agregarlas a Common.js.  Cree su propia versión de Common.js, guárdela en una ruta de acceso común y, a continuación, asigne esa ruta a SCRIPT\_COMMON\_PATH en el [archivo .vsz](../ide/dot-vsz-file-project-control.md).  
  
> [!NOTE]
>  Los asistentes incluidos en Visual C\+\+ usan las funciones de JScript presentes en Common.js.  Si cambia estas funciones, los asistentes de Visual C\+\+ pueden comportarse de forma inesperada.  
  
 Para obtener más información acerca de JScript, vea [Writing, Compiling, and Debugging JScript Code](http://msdn.microsoft.com/es-es/13e57e7d-4867-4555-b9e4-fc24aa75e628).  
  
## Depurar script  
 Para depurar script en archivos html del asistente, debe habilitar la depuración de script.  
  
#### Para habilitar la depuración de script  
  
1.  En Internet Explorer, haga clic en el menú **Herramientas** y elija **Opciones de Internet**.  
  
2.  Haga clic en la ficha **Opciones avanzadas**.  
  
3.  En la categoría **Examinar**, deshabilite la casilla **Deshabilitar depuración de script**.  
  
 De este modo, los archivos common.js y default.js también aparecerán en la ventana **Documentos en ejecución** al hacer clic en el botón Finalizar del asistente.  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)