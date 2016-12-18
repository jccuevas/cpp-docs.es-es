---
title: "Moving a String from One Resource File to Another | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "strings [C++], moving between files"
  - "resource script files, moving strings"
  - "string editing, moving strings between resources"
  - "String editor, moving strings between files"
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Moving a String from One Resource File to Another
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para mover una cadena de un archivo de script de recursos a otro  
  
1.  Abra la tabla de cadenas en los dos archivos .rc.  Para obtener más información, vea [Ver recursos en un archivo de script de recursos fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Haga clic con el botón secundario en la cadena que desee mover y elija **Cortar** en el menú contextual.  
  
3.  Sitúe el cursor en la ventana del **Editor de cadenas** de destino.  
  
4.  En el archivo .rc al que desee mover la cadena, haga clic con el botón secundario del mouse y elija **Pegar** en el menú contextual.  
  
    > [!NOTE]
    >  Si el valor de las propiedades **ID** o **Value** de la cadena desplazada entra en conflicto con otros valores **ID** o **Value** ya existentes del archivo de destino, se cambiará el valor **ID** o **Value** de la cadena desplazada.  Si ya existe una cadena con el mismo **ID**, se cambiará el **ID** de la cadena desplazada.  Si ya existe una cadena con el mismo **Value**, se cambiará el **Value** de la cadena desplazada.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados \(los orientados a Common Language Runtime\), vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [String Editor](../mfc/string-editor.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Personalizar los diseños de ventana](../Topic/Customizing%20window%20layouts%20in%20Visual%20Studio.md)   
 [Cadenas](_win32_Strings)   
 [Acerca de cadenas](_win32_About_Strings_cpp)