---
title: "Archivos de inclusi&#243;n de recursos (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.resourceincludes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Archivos de inclusión de recursos (cuadro de diálogo)"
  - "archivos rc, cambiar de almacenamiento"
  - "archivos de encabezado de símbolos, cambiar"
  - "compilar código fuente, incluir recursos"
  - "archivos .rc, cambiar de almacenamiento"
  - "archivos de encabezado de símbolos, solo lectura"
  - "símbolos, archivos de encabezado de símbolos"
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos de inclusi&#243;n de recursos (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede usar el cuadro de diálogo **Archivos de inclusión de recursos** para cambiar el hábito del entorno de almacenar todos los recursos en el archivo .rc del proyecto y todos los [símbolos](../mfc/symbols-resource-identifiers.md) en Resource.h.  
  
 Para abrir el cuadro de diálogo **Archivos de inclusión de recursos**, haga clic con el botón derecho en un archivo .rc de la [Vista de recursos](../windows/resource-view-window.md) y, a continuación, elija **Archivos de inclusión de recursos** en el menú contextual.  
  
 **Archivo de encabezado de símbolos**  
 Permite cambiar el nombre del archivo de encabezado donde se almacenan las definiciones de los símbolos del archivo de recursos.  Para obtener más información, vea [Cambiar los nombres de los archivos de encabezado de símbolos](../windows/changing-the-names-of-symbol-header-files.md).  
  
 **Directivas de símbolos de solo lectura**  
 Permite incluir archivos de encabezado cuyos símbolos no deberían modificarse durante una sesión de edición.  Por ejemplo, se puede incluir un archivo de símbolos compartido por varios proyectos.  También se pueden incluir archivos .h de MFC.  Para obtener más información, vea [Incluir símbolos compartidos \(de solo lectura\) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).  
  
 **Directivas de tiempo de compilación**  
 Permite incluir archivos de recursos creados y editados con independencia de los recursos del archivo principal de recursos, con directivas de tiempo de compilación \(como las que incluyen de forma condicional recursos\) o con recursos en formato personalizado.  Asimismo, el cuadro Directivas de tiempo de compilación puede usarse para incluir archivos de recursos de MFC estándar.  Para obtener más información, vea [Incluir recursos en tiempo de compilación](../Topic/How%20to:%20Include%20Resources%20at%20Compile%20Time.md).  
  
> [!NOTE]
>  Las entradas de estos cuadros de texto aparecen en el archivo .rc marcadas respectivamente por  `TEXTINCLUDE 1`, `TEXTINCLUDE 2` y `TEXTINCLUDE 3`.  Para obtener más información, vea [TN035: Usar varios archivos de recursos y archivos de encabezado con Visual C\+\+](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).  
  
 Una vez realizados los cambios en el archivo de recursos mediante el cuadro de diálogo **Archivos de inclusión de recursos**, deberá cerrar el archivo .rc y volver a abrirlo para que surtan efecto los cambios.  Para obtener más información, vea [Incluir recursos en tiempo de compilación](../Topic/How%20to:%20Include%20Resources%20at%20Compile%20Time.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [How to: Specify Include Directories for Resources](../windows/how-to-specify-include-directories-for-resources.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)