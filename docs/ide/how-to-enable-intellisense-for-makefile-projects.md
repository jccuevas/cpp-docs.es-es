---
title: "Cómo: habilitar IntelliSense para proyectos de archivos MAKE | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fae3ec35259250f71ad672d9468b991033608ae4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Cómo: Habilitar IntelliSense para proyectos de archivos MAKE
IntelliSense no funciona en el IDE para proyectos de archivos MAKE de Visual C++ cuando determinados configuración del proyecto o las opciones del compilador se configuran incorrectamente. Utilice este procedimiento para configurar proyectos de archivos MAKE de Visual C++, de modo que IntelliSense funcione cuando los proyectos de archivo MAKE que estén abiertos en el entorno de desarrollo de Visual Studio.  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>Para habilitar IntelliSense para proyectos de archivos MAKE en el IDE  
  
1.  Abra la **páginas de propiedades** cuadro de diálogo. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Seleccione el **NMake** propiedad página y, a continuación, modificar las propiedades en **IntelliSense** según corresponda.  
  
    -   Establecer el **definiciones de preprocesador** propiedad para definir los símbolos de preprocesador en el proyecto de archivos MAKE. Vea [/D (definiciones de preprocesador)](../build/reference/d-preprocessor-definitions.md), para obtener más información.  
  
    -   Establecer el **incluyen la ruta de búsqueda** propiedad para especificar la lista de directorios que el compilador debe buscar para resolver las referencias a archivos que se pasan a directivas de preprocesador en el proyecto de archivos MAKE. Vea [/I (directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md), para obtener más información.  
  
         Para los proyectos que se generan mediante CL. EXE desde una ventana de comandos, establezca la **INCLUDE** variable de entorno para especificar los directorios que el compilador debe buscar para resolver las referencias a archivos que se pasan a directivas de preprocesador en el proyecto de archivos MAKE.  
  
    -   Establecer el **forzado incluye** propiedad para especificar qué archivos de encabezado al proceso al generar el proyecto de archivos MAKE. Vea [/FI (el nombre Forced Include File)](../build/reference/fi-name-forced-include-file.md), para obtener más información.  
  
    -   Establecer el **ruta de acceso de búsqueda de ensamblado** propiedad para especificar la lista de directorios que el compilador debe buscar para resolver las referencias a ensamblados de .NET en el proyecto. Vea [/AI (especificar directorios de metadatos)](../build/reference/ai-specify-metadata-directories.md), para obtener más información.  
  
    -   Establecer el **ensamblados de uso forzados** propiedad para especificar qué ensamblados .NET para procesar al generar el proyecto de archivos MAKE. Vea [/FU (Name Forced #using archivo)](../build/reference/fu-name-forced-hash-using-file.md), para obtener más información.  
  
    -   Establecer el **opciones adicionales** propiedad para especificar otros modificadores de compilador que usará Intellisense al analizar los archivos de C++.  
  
4.  Haga clic en **Aceptar** para cerrar las páginas de propiedades.  
  
5.  Use la **guardar todo** comando para guardar la configuración de proyecto modificado.  
  
 La próxima vez abra el proyecto de archivos MAKE en el entorno de desarrollo de Visual Studio, ejecute el **Limpiar solución** comando y, a continuación, el **generar solución** comando en el proyecto de archivos MAKE. IntelliSense debería funcionar correctamente en el IDE.  
  
## <a name="see-also"></a>Vea también  
 [Usar IntelliSense](/visualstudio/ide/using-intellisense)   
 [Referencia de NMAKE](../build/nmake-reference.md)   
 [Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)