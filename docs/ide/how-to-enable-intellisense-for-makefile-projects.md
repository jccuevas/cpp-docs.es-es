---
title: 'Cómo: Habilitar IntelliSense para proyectos de archivos Make | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b9b11f04f1fe8d201d6d07ca5ed83f9ca7d991b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705467"
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Cómo: Habilitar IntelliSense para proyectos de archivos MAKE
IntelliSense no funciona en el IDE para proyectos de archivos Make de Visual C++ cuando no se configuran de manera correcta determinados valores del proyecto u opciones del compilador. Use este procedimiento para configurar proyectos de archivos Make de Visual C++, de modo que IntelliSense funcione cuando los proyectos de archivos Make se abran en el entorno de desarrollo de Visual Studio.  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>Para habilitar IntelliSense para proyectos de archivo Make en el IDE  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades**. Para obtener más información, vea [Trabajar con propiedades del proyecto](../ide/working-with-project-properties.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Seleccione la página de propiedades **NMake** y, después, modifique las propiedades en **IntelliSense** según corresponda.  
  
    -   Establezca la propiedad **Definiciones de preprocesador** para definir los símbolos de preprocesador en el proyecto de archivo Make. Vea [/D (Definiciones de preprocesador)](../build/reference/d-preprocessor-definitions.md) para obtener más información.  
  
    -   Establezca la propiedad **Ruta de acceso de búsqueda de inclusión** para especificar la lista de directorios en los que el compilador debe buscar para resolver las referencias de archivo que se pasan a las directivas de preprocesador en el proyecto de archivo Make. Vea [/I (Directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md) para obtener más información.  
  
         Para los proyectos que se compilan mediante CL.EXE desde una ventana de comandos, establezca la variable de entorno **INCLUDE** para especificar los directorios en los que el compilador debe buscar para resolver las referencias de archivo que se pasan a las directivas de preprocesador en el proyecto de archivo Make.  
  
    -   Establezca la propiedad **Archivos de inclusión forzados** para especificar qué archivos de encabezado se van a procesar al compilar el proyecto de archivo Make. Vea [/FI (Dar nombre al archivo de inclusión obligatorio)](../build/reference/fi-name-forced-include-file.md) para obtener más información.  
  
    -   Establezca la propiedad **Ruta de acceso de búsqueda de ensamblado** para especificar la lista de directorios que el compilador debe buscar para resolver las referencias a los ensamblados .NET del proyecto. Vea [/AI (Especificar directorios de metadatos)](../build/reference/ai-specify-metadata-directories.md) para obtener más información.  
  
    -   Establezca la propiedad **Ensamblados de uso forzados** para especificar qué ensamblados .NET se van a procesar al compilar el proyecto de archivo Make. Vea [/FU (Dar nombre al archivo #using obligatorio)](../build/reference/fu-name-forced-hash-using-file.md) para obtener más información.  
  
    -   Establezca la propiedad **Opciones adicionales** para especificar modificadores de compilador adicionales que IntelliSense usará al analizar los archivos de C++.  
  
4.  Haga clic en **Aceptar** para cerrar las páginas de propiedades.  
  
5.  Use el comando **Guardar todo** para guardar la configuración de proyecto modificada.  
  
 La próxima vez que abra el proyecto de archivo Make en el entorno de desarrollo de Visual Studio, ejecute los comandos **Limpiar solución** y **Compilar solución**. IntelliSense debería funcionar correctamente en el IDE.  
  
## <a name="see-also"></a>Vea también  
 [Usar IntelliSense](/visualstudio/ide/using-intellisense)   
 [Referencia de NMAKE](../build/nmake-reference.md)   
 [Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)