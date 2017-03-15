---
title: "Editing a String in a Version Information Resource | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "version information resources"
  - "resources [Visual Studio], editing version information"
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Editing a String in a Version Information Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para editar una cadena en un recurso de información de versión  
  
1.  Haga clic en el elemento una vez para seleccionarlo y luego comience a editarlo. Realice los cambios directamente en la tabla Información de versión o en la [ventana Propiedades](../Topic/Properties%20Window.md). Los cambios que realice se reflejarán en ambos lugares.  
  
     **Nota** Al editar la clave **FILEFLAGS** en el editor de la Información de versión, observará que no puede establecer la propiedades **Depuración**, **Compilación privada** o **Compilación especial** \(en la ventana Propiedades\) para archivos .rc:  
  
    -   El editor Información de versión establece la propiedad **Depuración** con \#ifdef en el script de recursos, según la marca de compilación **\_DEBUG**.  
  
    -   Si la clave **Compilación privada** tiene un **Valor** establecido en la tabla Información de versión, la propiedad **Compilación privada** correspondiente \(en la ventana Propiedades\) de la clave **FILEFLAGS** será **True**. Si el **Valor** está vacío, la propiedad será **False**. Del mismo modo, la clave **Compilación especial** \(en la tabla Información de versión\) está vinculada a la propiedad **Compilación especial** para la clave **FILEFLAGS**.  
  
 Para ordenar la secuencia de información del bloque de cadenas, haga clic en los encabezados de columna Clave o Valor. Estos encabezados reorganizan automáticamente la información en la secuencia seleccionada.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [Version Information Editor](../mfc/version-information-editor.md)   
 [Información de versiones \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)