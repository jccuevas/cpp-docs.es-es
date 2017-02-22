---
title: "CMFCTabDropTarget Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTabDropTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabDropTarget class"
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCTabDropTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona el mecanismo de comunicación entre un control de ficha y bibliotecas de OLE.  
  
## Sintaxis  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCTabDropTarget::OnDragEnter](../Topic/CMFCTabDropTarget::OnDragEnter.md)|Llamado por el marco cuando el usuario arrastra un objeto en una ventana de la pestaña.  \(Reemplaza [COleDropTarget::OnDragEnter](../Topic/COleDropTarget::OnDragEnter.md).\)|  
|[CMFCTabDropTarget::OnDragLeave](../Topic/CMFCTabDropTarget::OnDragLeave.md)|Llamado por el marco cuando el usuario arrastra un objeto fuera de la ventana de ficha que tiene el foco.  \(Reemplaza [COleDropTarget::OnDragLeave](../Topic/COleDropTarget::OnDragLeave.md).\)|  
|[CMFCTabDropTarget::OnDragOver](../Topic/CMFCTabDropTarget::OnDragOver.md)|Llamado por el marco cuando el usuario arrastra un objeto a la ventana de la pestaña que tiene el foco.  \(Reemplaza [COleDropTarget::OnDragOver](../Topic/COleDropTarget::OnDragOver.md).\)|  
|[CMFCTabDropTarget::OnDropEx](../Topic/CMFCTabDropTarget::OnDropEx.md)|Llamado por el marco cuando el usuario suelta el botón del mouse en el final de una operación de arrastre.  \(Reemplaza [COleDropTarget::OnDropEx](../Topic/COleDropTarget::OnDropEx.md).\)|  
|[CMFCTabDropTarget::Register](../Topic/CMFCTabDropTarget::Register.md)|Registra el control como una que puede ser el destino de una operación de arrastrar y colocar de OLE.|  
  
### Comentarios  
 Esta clase proporciona compatibilidad de arrastrar y colocar en la clase de `CMFCBaseTabCtrl` .  Si se inicializa la aplicación las bibliotecas VIEJAS mediante [AfxOleInit](../Topic/AfxOleInit.md) funcionan, los objetos de `CMFCBaseTabCtrl` se registran para operaciones de arrastrar y colocar.  
  
 La clase de `CMFCTabDropTarget` extiende la clase base creando la pestaña que está situado bajo el cuando una operación de arrastre produce el activo.  Para obtener más información sobre las operaciones de arrastrar y colocar, vea [Arrastrar y colocar \(OLE\)](../../mfc/drag-and-drop-ole.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCTabDropTarget` y usar el método de `Register` .  
  
 [!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/CPP/cmfctabdroptarget-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)  
  
 [CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)  
  
## Requisitos  
 **encabezado:** afxbasetabctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Arrastrar y colocar \(OLE\)](../../mfc/drag-and-drop-ole.md)