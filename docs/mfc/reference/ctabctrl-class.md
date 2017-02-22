---
title: "CTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabCtrl class"
  - "CTabCtrl class, controles comunes"
  - "controles de fichas"
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control común de la pestaña de Windows.  
  
## Sintaxis  
  
```  
class CTabCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabCtrl::CTabCtrl](../Topic/CTabCtrl::CTabCtrl.md)|Crea un objeto `CTabCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabCtrl::AdjustRect](../Topic/CTabCtrl::AdjustRect.md)|Calcula el área de presentación de un control de ficha dado un rectángulo de ventana, o calcula el rectángulo de ventana que corresponde a un área de presentación determinada.|  
|[CTabCtrl::Create](../Topic/CTabCtrl::Create.md)|Crea un control de ficha y lo adjunta a una instancia de un objeto de `CTabCtrl` .|  
|[CTabCtrl::CreateEx](../Topic/CTabCtrl::CreateEx.md)|Crea un control de la pestaña con Windows especificado extendidas los estilos y lo adjunta a una instancia de un objeto de `CTabCtrl` .|  
|[CTabCtrl::DeleteAllItems](../Topic/CTabCtrl::DeleteAllItems.md)|Quita todos los elementos de una pestaña.|  
|[CTabCtrl::DeleteItem](../Topic/CTabCtrl::DeleteItem.md)|Quita un elemento de una pestaña.|  
|[CTabCtrl::DeselectAll](../Topic/CTabCtrl::DeselectAll.md)|Elementos de los reinicios en un control de ficha, a las que se hizo clic.|  
|[CTabCtrl::DrawItem](../Topic/CTabCtrl::DrawItem.md)|Dibuja un elemento especificado de una pestaña.|  
|[CTabCtrl::GetCurFocus](../Topic/CTabCtrl::GetCurFocus.md)|Recupera la pestaña con el foco actual de una pestaña.|  
|[CTabCtrl::GetCurSel](../Topic/CTabCtrl::GetCurSel.md)|Determina la pestaña actualmente seleccionada en un control de la pestaña.|  
|[CTabCtrl::GetExtendedStyle](../Topic/CTabCtrl::GetExtendedStyle.md)|Recupera los estilos extendidos que están actualmente en uso para el control de la pestaña.|  
|[CTabCtrl::GetImageList](../Topic/CTabCtrl::GetImageList.md)|Recupera la lista de imágenes asociada a un control de la pestaña.|  
|[CTabCtrl::GetItem](../Topic/CTabCtrl::GetItem.md)|Información de recupera sobre una pestaña de un control de ficha.|  
|[CTabCtrl::GetItemCount](../Topic/CTabCtrl::GetItemCount.md)|Recupera el número de fichas en el control de ficha.|  
|[CTabCtrl::GetItemRect](../Topic/CTabCtrl::GetItemRect.md)|Recupera el rectángulo delimitador de una pestaña en un control de la pestaña.|  
|[CTabCtrl::GetItemState](../Topic/CTabCtrl::GetItemState.md)|Recupera el estado del elemento indicado de control de la pestaña.|  
|[CTabCtrl::GetRowCount](../Topic/CTabCtrl::GetRowCount.md)|Recupera el número de filas actual de pestañas en un control de la pestaña.|  
|[CTabCtrl::GetToolTips](../Topic/CTabCtrl::GetToolTips.md)|Recupera el identificador del control de información sobre herramientas asociado a un control de ficha.|  
|[CTabCtrl::HighlightItem](../Topic/CTabCtrl::HighlightItem.md)|Establece el estado del resaltado de un elemento de la pestaña.|  
|[CTabCtrl::HitTest](../Topic/CTabCtrl::HitTest.md)|Determina que la pestaña, si existe, en una posición especificada de la pantalla.|  
|[CTabCtrl::InsertItem](../Topic/CTabCtrl::InsertItem.md)|Inserta una nueva pestaña en un control de la pestaña.|  
|[CTabCtrl::RemoveImage](../Topic/CTabCtrl::RemoveImage.md)|Quita una imagen de lista de imágenes de una pestaña.|  
|[CTabCtrl::SetCurFocus](../Topic/CTabCtrl::SetCurFocus.md)|Establece el foco a una pestaña especificada en un control de la pestaña.|  
|[CTabCtrl::SetCurSel](../Topic/CTabCtrl::SetCurSel.md)|Selecciona una ficha en un control de ficha.|  
|[CTabCtrl::SetExtendedStyle](../Topic/CTabCtrl::SetExtendedStyle.md)|Establece los estilos extendidos para un control de la pestaña.|  
|[CTabCtrl::SetImageList](../Topic/CTabCtrl::SetImageList.md)|Asigna una lista de imágenes a un control de ficha.|  
|[CTabCtrl::SetItem](../Topic/CTabCtrl::SetItem.md)|Establece algunos o todos los atributos de una pestaña.|  
|[CTabCtrl::SetItemExtra](../Topic/CTabCtrl::SetItemExtra.md)|Establece el número de bytes por la pestaña reservada para los datos definidos por la aplicación en un control de la pestaña.|  
|[CTabCtrl::SetItemSize](../Topic/CTabCtrl::SetItemSize.md)|Establece el ancho y alto de un elemento.|  
|[CTabCtrl::SetItemState](../Topic/CTabCtrl::SetItemState.md)|Establece el estado del elemento indicado de control de la pestaña.|  
|[CTabCtrl::SetMinTabWidth](../Topic/CTabCtrl::SetMinTabWidth.md)|Establece el ancho mínimo de elementos en un control de la pestaña.|  
|[CTabCtrl::SetPadding](../Topic/CTabCtrl::SetPadding.md)|Establece la cantidad de espacio \(relleno\) alrededor del icono y la etiqueta de cada pestaña de un control de ficha.|  
|[CTabCtrl::SetToolTips](../Topic/CTabCtrl::SetToolTips.md)|Asigna un control de información sobre herramientas a un control de ficha.|  
  
## Comentarios  
 Un “control de la pestaña” es análogo a los divisores de un bloc de notas o las etiquetas de un archivo.CAB.  Utilizando un control de ficha, una aplicación puede definir varias páginas para la misma área de una ventana o cuadro de diálogo.  Cada página consta de un conjunto de información o de un grupo de controles que la aplicación muestre cuando el usuario selecciona la pestaña correspondiente.  Un tipo especial de control de la pestaña muestra las pestañas que parecen los botones.  Hacer clic en un botón debe inmediatamente realizar un comando en lugar de mostrar una página.  
  
 Este control \(y por consiguiente la clase de `CTabCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 Para obtener más información sobre cómo utilizar `CTabCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CTabCtrl](../../mfc/using-ctabctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CHeaderCtrl Class](../../mfc/reference/cheaderctrl-class.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)