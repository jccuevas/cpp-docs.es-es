---
title: "Changing a Symbol&#39;s Numeric Value | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.changing.value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numeric values"
  - "symbols, numeric values"
  - "numeric values, changing symbols"
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Changing a Symbol&#39;s Numeric Value
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En los símbolos asociados a un único recurso, puede usar la [ventana Propiedades](../Topic/Properties%20Window.md) para cambiar el valor de símbolo.  Puede usar el [cuadro de diálogo Símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar el valor de los símbolos que no estén asignados a un recurso.  Para obtener más información, vea [Cambiar símbolos sin asignar](../Topic/Changing%20Unassigned%20Symbols.md).  
  
### Para cambiar el valor de un símbolo asignado a un solo recurso u objeto  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), seleccione el recurso.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En la ventana **Propiedades**, escriba el nombre del símbolo seguido de un signo igual y un número entero en el cuadro **Id.**, por ejemplo:  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 El nuevo valor se almacena en el archivo de encabezado de símbolos la próxima vez que guarde el proyecto.  En el cuadro Id. solo está visible el nombre del símbolo; el signo igual y el valor no se muestran después de su validación.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Symbol Value Restrictions](../Topic/Symbol%20Value%20Restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)