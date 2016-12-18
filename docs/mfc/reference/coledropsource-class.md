---
title: "COleDropSource Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDropSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDropSource class"
  - "arrastrar y colocar, drop source"
  - "operaciones de arrastre"
  - "drop target, dragging data to"
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDropSource Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite que los datos se arrastran a un destino.  
  
## Sintaxis  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](../Topic/COleDropSource::COleDropSource.md)|Crea un objeto `COleDropSource`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](../Topic/COleDropSource::GiveFeedback.md)|Cambia el cursor durante una operación de arrastrar y colocar.|  
|[COleDropSource::OnBeginDrag](../Topic/COleDropSource::OnBeginDrag.md)|Captura del mouse de identificadores durante una operación de arrastrar y colocar.|  
|[COleDropSource::QueryContinueDrag](../Topic/COleDropSource::QueryContinueDrag.md)|Comprueba si el arrastrar debe continuar.|  
  
## Comentarios  
 La clase de [COleDropTarget](../../mfc/reference/coledroptarget-class.md) controla la parte receptora de la operación de arrastrar y colocar.  El objeto de `COleDropSource` es responsable de determinar cuando comienza una operación de arrastrar, de proporcionar comentarios durante la operación de arrastrar, y determinar cuándo finaliza la operación de arrastrar.  
  
 Para utilizar un objeto de `COleDropSource` , simplemente llame al constructor.  Esto simplifica el proceso de determinar qué eventos, como un clic del mouse, un comenzar una operación de arrastre mediante la función de [COleDataSource:: DoDragDrop](../Topic/COleDataSource::DoDragDrop.md), de [MFC:: DoDragDrop](../Topic/COleClientItem::DoDragDrop.md), o de [COleServerItem:: DoDragDrop](../Topic/COleServerItem::DoDragDrop.md) .  Estas funciones producirán un objeto de `COleDropSource` automáticamente.  Puede ser conveniente modificar el comportamiento predeterminado de las funciones reemplazable de `COleDropSource` .  Estas funciones miembro se llame en los tiempos adecuados para el marco.  
  
 Para obtener más información acerca de las operaciones de arrastrar y colocar mediante OLE, vea el artículo [Arrastrar y colocar \(OLE\)](../../mfc/drag-and-drop-ole.md).  
  
 Para obtener más información, vea [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)