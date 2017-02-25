---
title: "Actualizar datos con el control de datos ADO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ADO [C++], enlace de datos"
  - "ADO [C++], controles de datos"
ms.assetid: 8bec34b9-93dd-4872-b023-55ac011ccff5
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Actualizar datos con el control de datos ADO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los datos del control de datos ADO pueden ser de sólo lectura o modificables.  
  
### Para crear una aplicación que modifique datos mediante el control de datos ADO  
  
1.  Establezca el valor de la propiedad **CursorLocation** del control de datos ADO.  Las opciones son:  
  
    -   Lado del servidor  
  
    -   Lado del cliente  
  
2.  Establezca el valor de la propiedad **LockType** del control de datos ADO.  Se recomienda la simultaneidad simultánea optimista.  
  
3.  Establezca el valor de la propiedad **CursorType** del control de datos ADO.  Las opciones son:  
  
    -   Cursor de conjunto de claves  
  
    -   Cursor dinámico  
  
    -   Cursor estático  
  
     Compruebe que el proveedor OLE DB admite la opción elegida.  
  
4.  Si es necesario, establezca los valores de las propiedades del control enlazado a datos para permitir las actualizaciones.  Tenga en cuenta que algunos controles no permiten la actualización.  
  
 Para obtener más información sobre estas propiedades, consulte la documentación de ADO.  
  
## Vea también  
 [Enlace de datos de ADO](../../data/ado-rdo/ado-databinding.md)   
 [Utilizar el enlace de datos de ADO en Visual C\+\+](../../data/ado-rdo/using-ado-databinding-in-visual-cpp.md)