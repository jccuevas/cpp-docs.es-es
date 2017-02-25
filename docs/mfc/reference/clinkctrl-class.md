---
title: "CLinkCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CLinkCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinkCtrl class"
  - "controles [MFC], vínculos"
  - "vínculos [C++], link control"
  - "SysLink control"
  - "páginas web, link control"
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CLinkCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de controles comunes de Windows SysLink.  
  
## Sintaxis  
  
```  
class CLinkCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinkCtrl::CLinkCtrl](../Topic/CLinkCtrl::CLinkCtrl.md)|Crea un objeto `CLinkCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinkCtrl::Create](../Topic/CLinkCtrl::Create.md)|Crea un control de vínculos y lo asocia a un objeto de `CLinkCtrl` .|  
|[CLinkCtrl::CreateEx](../Topic/CLinkCtrl::CreateEx.md)|Crea un control de vínculos con estilos extendidos y lo asocia a un objeto de `CLinkCtrl` .|  
|[CLinkCtrl::GetIdealHeight](../Topic/CLinkCtrl::GetIdealHeight.md)|Recupera el alto ideal de control de vínculos.|  
|[CLinkCtrl::GetIdealSize](../Topic/CLinkCtrl::GetIdealSize.md)|Calcula el alto preferido de texto del vínculo del control de vínculos actual, dependiendo del ancho especificado de vínculo.|  
|[CLinkCtrl::GetItem](../Topic/CLinkCtrl::GetItem.md)|Recupera los estados y los atributos de un elemento de control de vínculos.|  
|[CLinkCtrl::GetItemID](../Topic/CLinkCtrl::GetItemID.md)|Recupera el identificador de un elemento de control de vínculos.|  
|[CLinkCtrl::GetItemState](../Topic/CLinkCtrl::GetItemState.md)|Recupera el estado del elemento de control de vínculos.|  
|[CLinkCtrl::GetItemUrl](../Topic/CLinkCtrl::GetItemUrl.md)|Recupera la dirección URL representada por el elemento de control de vínculos.|  
|[CLinkCtrl::HitTest](../Topic/CLinkCtrl::HitTest.md)|Determina si el usuario hizo clic en el vínculo especificado.|  
|[CLinkCtrl::SetItem](../Topic/CLinkCtrl::SetItem.md)|Establece los estados y los atributos de un elemento de control de vínculos.|  
|[CLinkCtrl::SetItemID](../Topic/CLinkCtrl::SetItemID.md)|Establece el identificador de un elemento de control de vínculos.|  
|[CLinkCtrl::SetItemState](../Topic/CLinkCtrl::SetItemState.md)|Establece el estado del elemento de control de vínculos.|  
|[CLinkCtrl::SetItemUrl](../Topic/CLinkCtrl::SetItemUrl.md)|Establece la dirección URL representada por el elemento de control de vínculos.|  
  
## Comentarios  
 Un “control de vínculos” proporciona una manera cómoda de insertar vínculos de hipertexto en una ventana.  El control real es una ventana que representa el texto anotado e inicia aplicaciones adecuadas cuando el usuario hace clic en un vínculo incrustado.  Varios vínculos se admiten dentro de un control y pueden tener acceso a un índice de base cero.  
  
 Este control \(y por consiguiente la clase de `CLinkCtrl` \) sólo está disponible para los programas que se ejecutan en Windows XP y posterior.  
  
 Para obtener más información, vea [Control de SysLink](http://msdn.microsoft.com/library/windows/desktop/bb760706) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CLinkCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)