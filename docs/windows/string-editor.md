---
title: "String Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.string.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "String editor"
  - "string tables"
  - "string tables, String editor"
  - "string editing"
  - "string editing, string tables"
  - "resource editors, String editor"
  - "strings [C++], editing"
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# String Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una tabla de cadenas es un recurso de Windows que contiene una lista de id., valores y títulos para todas las cadenas de su aplicación. Por ejemplo, los mensajes de la barra de estado se encuentran en la tabla de cadenas.  
  
 Al desarrollar una aplicación, puede tener varias tablas de cadenas: una para cada idioma o condición. Sin embargo, un módulo ejecutable solo tiene una tabla de cadenas. Una aplicación en ejecución puede hacer referencia a varias tablas de cadenas si coloca las tablas en varias DLL diferentes.  
  
 Las tablas de cadenas facilitan la localización de la aplicación en diferentes idiomas. Si todas las cadenas se encuentran en una tabla de cadenas, puede localizar la aplicación mediante la traducción de las cadenas \(y otros recursos\) sin cambiar el código fuente. Esto suele ser más deseable que buscar y reemplazar manualmente las distintas cadenas en archivos de código fuente.  
  
 Con el editor de cadenas, puede:  
  
-   [Buscar una o más cadenas](../mfc/finding-a-string.md).  
  
-   [Insertar entradas nuevas](../mfc/adding-or-deleting-a-string.md) rápidamente en la tabla de cadenas.  
  
-   [Mover una cadena de un archivo de recursos a otro](../mfc/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [Usar la edición en contexto para las propiedades ID, Value y Caption](../mfc/changing-the-properties-of-a-string.md) y ver los cambios inmediatamente.  
  
-   [Cambiar la propiedad caption de varias cadenas](../mfc/changing-the-caption-property-of-multiple-strings.md)  
  
-   [Agregar formato o caracteres especiales a una cadena](../mfc/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows no permite la creación de tablas de cadenas vacías. Si crea una tabla de cadenas sin entradas, se elimina automáticamente al guardar el archivo de recursos.  
  
 Para información sobre cómo agregar recursos a proyectos administrados \(aquellos que tienen como objeto Common Language Runtime\), vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Resource Editors](../mfc/resource-editors.md)   
 [Cadenas](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [Acerca de las cadenas](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)