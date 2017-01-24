---
title: "Clase CMFCDynamicLayout | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: 16
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase CMFCDynamicLayout
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica cómo se mueven y cambian de tamaño los controles de una ventana cuando el usuario cambia el tamaño de la ventana.  
  
## Sintaxis  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|Construye un objeto `CMFCDynamicLayout`.|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destructor.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCDynamicLayout::AddItem](../Topic/CMFCDynamicLayout::AddItem.md)|Agrega una ventana secundaria \(un control, normalmente\) a la lista de ventanas controladas por el administrador de diseño dinámico.|  
|[CMFCDynamicLayout::Adjust](../Topic/CMFCDynamicLayout::Adjust.md)|Agrega una ventana secundaria \(un control, normalmente\) a la lista de ventanas controladas por el administrador de diseño dinámico.|  
|[CMFCDynamicLayout::Create](../Topic/CMFCDynamicLayout::Create.md)|Almacena y valida la ventana host.|  
|[CMFCDynamicLayout::GetHostWnd](../Topic/CMFCDynamicLayout::GetHostWnd.md)|Devuelve un puntero a una ventana host.|  
|[CMFCDynamicLayout::GetMinSize](../Topic/CMFCDynamicLayout::GetMinSize.md)|Devuelve el tamaño de la ventana por debajo del cual no se ajusta el diseño.|  
|[CMFCDynamicLayout::GetWindowRect](../Topic/CMFCDynamicLayout::GetWindowRect.md)|Recupera el rectángulo de área de cliente actual de la ventana.|  
|[CMFCDynamicLayout::HasItem](../Topic/CMFCDynamicLayout::HasItem.md)|Comprueba si se agregó un control secundario al diseño dinámico.|  
|[CMFCDynamicLayout::IsEmpty](../Topic/CMFCDynamicLayout::IsEmpty.md)|Comprueba si un diseño dinámico no tiene ventanas secundarias agregadas.|  
|[CMFCDynamicLayout::LoadResource](../Topic/CMFCDynamicLayout::LoadResource.md)|Lee el diseño dinámico del recurso AFX\_DIALOG\_LAYOUT y después aplica el diseño a la ventana del host.|  
|[CMFCDynamicLayout::MoveHorizontal](../Topic/CMFCDynamicLayout::MoveHorizontal.md) estático|Obtiene un valor [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) que define cuánto se mueve horizontalmente un control secundario cuando el usuario cambia el tamaño de su ventana de hospedaje.|  
|[CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md) estático|Obtiene un valor [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) que define cuánto se mueve horizontalmente un control secundario cuando el usuario cambia el tamaño de su ventana de hospedaje.|  
|[CMFCDynamicLayout::MoveNone](../Topic/CMFCDynamicLayout::MoveNone.md) estático|Obtiene un valor [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) que no representa ningún movimiento, vertical u horizontal, de un control secundario.|  
|[CMFCDynamicLayout::MoveVertical](../Topic/CMFCDynamicLayout::MoveVertical.md) estático|Obtiene un valor [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) que define cuánto se mueve verticalmente un control secundario cuando el usuario cambia el tamaño de su ventana de hospedaje.|  
|[CMFCDynamicLayout::SetMinSize](../Topic/CMFCDynamicLayout::SetMinSize.md)|Establece el tamaño de la ventana por debajo del cual no se ajusta el diseño.|  
|[CMFCDynamicLayout::SizeHorizontal](../Topic/CMFCDynamicLayout::SizeHorizontal.md) estático|Obtiene un valor [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) que define cuánto se redimensiona horizontalmente un control secundario cuando el usuario cambia el tamaño de su ventana de hospedaje.|  
|[CMFCDynamicLayout::SizeHorizontalAndVertical](../Topic/CMFCDynamicLayout::SizeHorizontalAndVertical.md) estático|Obtiene un valor [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) que define cuánto se redimensiona horizontalmente un control secundario cuando el usuario cambia el tamaño de su ventana de hospedaje.|  
|[CMFCDynamicLayout::SizeNone](../Topic/CMFCDynamicLayout::SizeNone.md) estático|Obtiene un valor [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) que no representa cambios de tamaño para un control secundario.|  
|[CMFCDynamicLayout::SizeVertical](../Topic/CMFCDynamicLayout::SizeVertical.md) estático|Obtiene un valor [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) que define cuánto se redimensiona verticalmente un control secundario cuando el usuario cambia el tamaño de su ventana de hospedaje.|  
  
## Tipos anidados  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCDynamicLayout::MoveSettings \(Estructura\)](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md)|Encapsula los datos de movimiento de los controles de un diseño dinámico.|  
|[Estructura de CMFCDynamicLayout::SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md)|Encapsula los datos de cambio de tamaño de los controles de un diseño dinámico.|  
  
## Comentarios  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## Requisitos  
 **Encabezado:** afxlayout.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)