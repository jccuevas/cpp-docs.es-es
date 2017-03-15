---
title: "C&#243;mo: Habilitar IntelliSense para proyectos de archivos MAKE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCNMakeTool.IntelliSense"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IntelliSense, proyectos de archivos Make"
  - "proyectos de archivos Make, IntelliSense"
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Habilitar IntelliSense para proyectos de archivos MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

IntelliSense no funciona en el IDE de los proyectos de archivos MAKE de Visual C\+\+ si ciertas opciones de configuración del proyecto o del compilador están definidas incorrectamente.  Utilice este procedimiento para configurar los proyectos de archivos MAKE de Visual C\+\+, para que IntelliSense funcione cuando se abran los proyectos de archivos MAKE en el entorno de desarrollo de Visual Studio.  
  
### Para habilitar IntelliSense para los proyectos de archivos MAKE en el IDE  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades**.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Seleccione la página de propiedades **NMake** y, a continuación, modifique las propiedades según corresponda bajo **IntelliSense**.  
  
    -   Establezca la propiedad **Definiciones del preprocesador** para definir cualquier símbolo de preprocesador en el proyecto de archivo MAKE.  Vea [\/D \(Definiciones de preprocesador\)](../build/reference/d-preprocessor-definitions.md), para obtener más información.  
  
    -   Establezca la propiedad **Ruta de acceso de búsqueda de inclusión** para especificar la lista de directorios que buscará el compilador con el fin de resolver referencias a archivos pasadas a directivas de preprocesador del proyecto de archivo MAKE.  Vea [\/I \(Directorios de inclusión adicionales\)](../build/reference/i-additional-include-directories.md), para obtener más información.  
  
         Para proyectos que se generan mediante CL.EXE desde una ventana de comandos, establezca la variable de entorno **INCLUDE** con el fin de especificar directorios que buscará el compilador para resolver referencias a archivos que se pasan a directivas de preprocesador del proyecto de archivo MAKE.  
  
    -   Establezca la propiedad **Archivos de inclusión forzados** para especificar qué archivos de encabezado desea procesar al compilar el proyecto de archivo MAKE.  Vea [\/FI \(Dar nombre al archivo de inclusión obligatorio\)](../build/reference/fi-name-forced-include-file.md), para obtener más información.  
  
    -   Establezca la propiedad **Ruta de acceso de búsqueda de ensamblado** para especificar la lista de directorios que buscará el compilador para resolver referencias a ensamblados .NET del proyecto.  Vea [\/AI \(Especificar directorios de metadatos\)](../build/reference/ai-specify-metadata-directories.md), para obtener más información.  
  
    -   Establezca la propiedad **Ensamblados de uso forzados** para especificar qué ensamblados .NET se desean procesar al compilar el proyecto de archivo MAKE.  Vea [\/FU \(Asignar nombre al archivo \#using obligatorio\)](../build/reference/fu-name-forced-hash-using-file.md), para obtener más información.  
  
    -   Establezca la propiedad **Opciones adicionales** para especificar otros modificadores de compilador que usará Intellisense al analizar los archivos de C\+\+.  
  
4.  Haga clic en **Aceptar** para cerrar las páginas de propiedades.  
  
5.  Utilice el comando **Guardar todo** para guardar la configuración del proyecto modificada.  
  
 La próxima vez que se abra el proyecto de archivo MAKE en el entorno de desarrollo de Visual Studio, habrá que ejecutar los comandos **Limpiar solución** y **Compilar solución** en el proyecto de archivo MAKE.  IntelliSense debería funcionar correctamente en el IDE.  
  
## Vea también  
 [Utilizar IntelliSense](../Topic/Using%20IntelliSense.md)   
 [Referencia de NMAKE](../build/nmake-reference.md)   
 [Cómo: Crear un proyecto de C\+\+ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)