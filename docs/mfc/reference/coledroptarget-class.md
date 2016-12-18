---
title: "COleDropTarget Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDropTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDropTarget class"
  - "arrastrar y colocar, drop target"
  - "drop commands"
  - "drop commands, aceptar"
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDropTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona el mecanismo de comunicación entre una ventana y bibliotecas VIEJAS.  
  
## Sintaxis  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](../Topic/COleDropTarget::COleDropTarget.md)|Crea un objeto `COleDropTarget`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](../Topic/COleDropTarget::OnDragEnter.md)|Llamado cuando el cursor primero entra en la ventana.|  
|[COleDropTarget::OnDragLeave](../Topic/COleDropTarget::OnDragLeave.md)|Llamado cuando el cursor se arrastran fuera de la ventana.|  
|[COleDropTarget::OnDragOver](../Topic/COleDropTarget::OnDragOver.md)|Denominado repetidamente cuando el cursor se arrastra a la ventana.|  
|[COleDropTarget::OnDragScroll](../Topic/COleDropTarget::OnDragScroll.md)|Denominado para determinar si el cursor se arrastra del área de desplazamiento de la ventana.|  
|[COleDropTarget::OnDrop](../Topic/COleDropTarget::OnDrop.md)|Llamado cuando se colocan los datos en la ventana, controlador predeterminado.|  
|[COleDropTarget::OnDropEx](../Topic/COleDropTarget::OnDropEx.md)|Llamado cuando se colocan los datos en la ventana, controlador inicial.|  
|[COleDropTarget::Register](../Topic/COleDropTarget::Register.md)|registra la ventana como destino válido.|  
|[COleDropTarget::Revoke](../Topic/COleDropTarget::Revoke.md)|Hace que la ventana para dejar de ser un destino de colocación válido.|  
  
## Comentarios  
 Crear un objeto de esta clase permite que una ventana acepte datos a través del mecanismo de arrastrar y colocar de OLE.  
  
 Para obtener una ventana para aceptar comandos de entrega, primero debe crear un objeto de clase de `COleDropTarget` , y después llama a la función de [Registrarse](../Topic/COleDropTarget::Register.md) con un puntero al objeto deseado de `CWnd` como único parámetro.  
  
 Para obtener más información acerca de las operaciones de arrastrar y colocar mediante OLE, vea el artículo [Arrastrar y colocar \(OLE\)](../../mfc/drag-and-drop-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDropSource Class](../../mfc/reference/coledropsource-class.md)