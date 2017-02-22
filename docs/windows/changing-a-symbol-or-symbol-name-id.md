---
title: "Changing a Symbol or Symbol Name (ID) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.changing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbol names"
  - "symbols, names"
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Changing a Symbol or Symbol Name (ID)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se crea un nuevo recurso u objeto de recurso, el entorno de desarrollo le asigna un nombre de símbolo predeterminado, por ejemplo, IDD\_DIALOG1.  Puede usar la [Ventana Propiedades](../Topic/Properties%20Window.md) para cambiar el nombre del símbolo predeterminado o para cambiar el nombre de cualquier símbolo ya asociado a un recurso.  
  
### Para cambiar el nombre del símbolo de un recurso  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), seleccione el recurso.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En la ventana **Propiedades**, escriba un nombre de símbolo nuevo o seleccione uno en la lista de símbolos existentes, en el cuadro **ID**.  
  
     Si escribe un nombre de símbolo nuevo, se le asigna automáticamente un valor.  
  
 Puede usar el [cuadro de diálogo Símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar los nombres de los símbolos que no estén asignados a un recurso.  Para obtener más información, consulte [Cambiar símbolos sin asignar](../Topic/Changing%20Unassigned%20Symbols.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, consulte [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Symbol Name Restrictions](../windows/symbol-name-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)