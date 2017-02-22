---
title: "CSliderCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSliderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSliderCtrl class"
  - "CSliderCtrl class, controles comunes"
  - "controles deslizantes, CSliderCtrl class"
  - "Windows common controls [C++], CSliderCtrl"
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CSliderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control común del control deslizante de Windows.  
  
## Sintaxis  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](../Topic/CSliderCtrl::CSliderCtrl.md)|Crea un objeto `CSliderCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](../Topic/CSliderCtrl::ClearSel.md)|Borra la selección actual en un control deslizante.|  
|[CSliderCtrl::ClearTics](../Topic/CSliderCtrl::ClearTics.md)|Quita las marcas de paso actuales de un control deslizante.|  
|[CSliderCtrl::Create](../Topic/CSliderCtrl::Create.md)|Crea un control deslizante y lo asocia a un objeto de `CSliderCtrl` .|  
|[CSliderCtrl::CreateEx](../Topic/CSliderCtrl::CreateEx.md)|Crea un control deslizante con Windows especificado extendidas estilos y lo asocia a un objeto de `CSliderCtrl` .|  
|[CSliderCtrl::GetBuddy](../Topic/CSliderCtrl::GetBuddy.md)|Recupera el identificador de una ventana de relacionada de control slider en una ubicación determinada.|  
|[CSliderCtrl::GetChannelRect](../Topic/CSliderCtrl::GetChannelRect.md)|Recupera el tamaño del canal de control slider.|  
|[CSliderCtrl::GetLineSize](../Topic/CSliderCtrl::GetLineSize.md)|Recupera el tamaño de la línea de un control deslizante.|  
|[CSliderCtrl::GetNumTics](../Topic/CSliderCtrl::GetNumTics.md)|Recupera el número de marcas de paso de un control deslizante.|  
|[CSliderCtrl::GetPageSize](../Topic/CSliderCtrl::GetPageSize.md)|Recupera el tamaño de página de un control deslizante.|  
|[CSliderCtrl::GetPos](../Topic/CSliderCtrl::GetPos.md)|Recupera la posición actual del control deslizante.|  
|[CSliderCtrl::GetRange](../Topic/CSliderCtrl::GetRange.md)|Recupera las posiciones límite de un control deslizante.|  
|[CSliderCtrl::GetRangeMax](../Topic/CSliderCtrl::GetRangeMax.md)|recupera la posición máxima para un control deslizante.|  
|[CSliderCtrl::GetRangeMin](../Topic/CSliderCtrl::GetRangeMin.md)|recupera la posición mínima para un control deslizante.|  
|[CSliderCtrl::GetSelection](../Topic/CSliderCtrl::GetSelection.md)|recupera el intervalo de la selección actual.|  
|[CSliderCtrl::GetThumbLength](../Topic/CSliderCtrl::GetThumbLength.md)|Recupera el control deslizante del control trackbar actual.|  
|[CSliderCtrl::GetThumbRect](../Topic/CSliderCtrl::GetThumbRect.md)|Recupera el tamaño del control de control slider.|  
|[CSliderCtrl::GetTic](../Topic/CSliderCtrl::GetTic.md)|recupera la posición de la marca de graduación especificada.|  
|[CSliderCtrl::GetTicArray](../Topic/CSliderCtrl::GetTicArray.md)|Recupera la matriz de posiciones de la marca de graduación para un control deslizante.|  
|[CSliderCtrl::GetTicPos](../Topic/CSliderCtrl::GetTicPos.md)|Recupera la posición de la marca de graduación especificada, en coordenadas de cliente.|  
|[CSliderCtrl::GetToolTips](../Topic/CSliderCtrl::GetToolTips.md)|Recupera el identificador al control de información sobre herramientas asignado al control deslizante, si existe.|  
|[CSliderCtrl::SetBuddy](../Topic/CSliderCtrl::SetBuddy.md)|Asigna una ventana como ventana de relacionada para un control deslizante.|  
|[CSliderCtrl::SetLineSize](../Topic/CSliderCtrl::SetLineSize.md)|Establece el tamaño de la línea de un control deslizante.|  
|[CSliderCtrl::SetPageSize](../Topic/CSliderCtrl::SetPageSize.md)|Establece el tamaño de página de un control deslizante.|  
|[CSliderCtrl::SetPos](../Topic/CSliderCtrl::SetPos.md)|Establece la posición actual del control deslizante.|  
|[CSliderCtrl::SetRange](../Topic/CSliderCtrl::SetRange.md)|Establece las posiciones límite de un control deslizante.|  
|[CSliderCtrl::SetRangeMax](../Topic/CSliderCtrl::SetRangeMax.md)|establece la posición máxima para un control deslizante.|  
|[CSliderCtrl::SetRangeMin](../Topic/CSliderCtrl::SetRangeMin.md)|establece la posición mínima para un control deslizante.|  
|[CSliderCtrl::SetSelection](../Topic/CSliderCtrl::SetSelection.md)|establece el intervalo de la selección actual.|  
|[CSliderCtrl::SetThumbLength](../Topic/CSliderCtrl::SetThumbLength.md)|Establece el alto del control deslizante del control trackbar actual.|  
|[CSliderCtrl::SetTic](../Topic/CSliderCtrl::SetTic.md)|establece la posición de la marca de graduación especificada.|  
|[CSliderCtrl::SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md)|Establece la frecuencia de marcas de paso por el incremento de control slider.|  
|[CSliderCtrl::SetTipSide](../Topic/CSliderCtrl::SetTipSide.md)|Coloca un control de información sobre herramientas utilizará un control trackbar.|  
|[CSliderCtrl::SetToolTips](../Topic/CSliderCtrl::SetToolTips.md)|Asigna un control de información sobre herramientas a un control deslizante.|  
  
## Comentarios  
 Un “control slider” \(también conocido como trackbar\) es una ventana que contiene un control deslizante y marcas de graduación opcionales.  Cuando el usuario mueve el control deslizante, utilizando el mouse o las teclas de dirección, el control envía mensajes de notificación para indicar el cambio.  
  
 Los controles deslizantes son útiles cuando se desea que el usuario seleccione un valor discreto o un conjunto de valores consecutivos en un rango.  Por ejemplo, puede utilizar un control deslizante para permitir que el usuario establezca la velocidad de repetición del teclado mueve el control deslizante hacia una marca de graduación determinada.  
  
 Este control \(y por consiguiente la clase de `CSliderCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 El control deslizante se desplaza en incrementos que especifica cuando se crea.  Por ejemplo, si especifica que el control deslizante debe tener un intervalo de cinco, el control deslizante puede ocupar sólo seis posiciones: una posición en el lado izquierdo del control y el control deslizante colocar para cada incremento en el intervalo.  Normalmente, cada una de estas posiciones se identifica mediante una marca de graduación.  
  
 Crea un control deslizante utilizando el constructor y la función miembro de **Crear** de `CSliderCtrl`.  Una vez creado un control deslizante, puede utilizar funciones miembro de `CSliderCtrl` para cambiar muchas de sus propiedades.  Cambios que puede realizar incluyen que establece las posiciones límite del control deslizante, marcas de graduación, de establecer un intervalo de selección, y colocando el control deslizante de nuevo.  
  
 Para obtener más información sobre cómo utilizar `CSliderCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo CMNCTRL2 de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl Class](../../mfc/reference/cprogressctrl-class.md)