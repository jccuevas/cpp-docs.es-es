---
title: "CHeaderCtrl Class | Microsoft Docs"
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
  - "CHeaderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeaderCtrl class"
  - "header controls, CHeaderCtrl class"
  - "Windows common controls [C++], CHeaderCtrl"
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
caps.latest.revision: 24
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHeaderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control de encabezado común de Windows.  
  
## Sintaxis  
  
```  
class CHeaderCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeaderCtrl::CHeaderCtrl](../Topic/CHeaderCtrl::CHeaderCtrl.md)|Crea un objeto `CHeaderCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeaderCtrl::ClearAllFilters](../Topic/CHeaderCtrl::ClearAllFilters.md)|borra todos los filtros para un control de encabezado.|  
|[CHeaderCtrl::ClearFilter](../Topic/CHeaderCtrl::ClearFilter.md)|borra el filtro para un control de encabezado.|  
|[CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md)|Crea un control de encabezado y lo asocia a un objeto de `CHeaderCtrl` .|  
|[CHeaderCtrl::CreateDragImage](../Topic/CHeaderCtrl::CreateDragImage.md)|Crea una versión transparente en la imagen de un elemento dentro de un control de encabezado.|  
|[CHeaderCtrl::CreateEx](../Topic/CHeaderCtrl::CreateEx.md)|Crea un control de encabezado con Windows especificado extendidas estilos y lo asocia a un objeto de `CListCtrl` .|  
|[CHeaderCtrl::DeleteItem](../Topic/CHeaderCtrl::DeleteItem.md)|elimina un elemento de un control de encabezado.|  
|[CHeaderCtrl::DrawItem](../Topic/CHeaderCtrl::DrawItem.md)|Dibuja el elemento especificado de un control de encabezado.|  
|[CHeaderCtrl::EditFilter](../Topic/CHeaderCtrl::EditFilter.md)|Inicio que edita el filtro especificado de un control de encabezado.|  
|[CHeaderCtrl::GetBitmapMargin](../Topic/CHeaderCtrl::GetBitmapMargin.md)|Recupera el ancho del margen de un mapa de bits en un control de encabezado.|  
|[CHeaderCtrl::GetFocusedItem](../Topic/CHeaderCtrl::GetFocusedItem.md)|Obtiene el identificador de elemento en el control de encabezado actual que tiene el foco.|  
|[CHeaderCtrl::GetImageList](../Topic/CHeaderCtrl::GetImageList.md)|Recupera el identificador de una imagen que se utiliza para dibujar elementos encabezado en un control de encabezado.|  
|[CHeaderCtrl::GetItem](../Topic/CHeaderCtrl::GetItem.md)|Recupera información sobre un elemento del control de encabezado.|  
|[CHeaderCtrl::GetItemCount](../Topic/CHeaderCtrl::GetItemCount.md)|recupera un recuento de los elementos en un control de encabezado.|  
|[CHeaderCtrl::GetItemDropDownRect](../Topic/CHeaderCtrl::GetItemDropDownRect.md)|Obtiene la información del rectángulo delimitador del botón desplegable especificado en un control de encabezado.|  
|[CHeaderCtrl::GetItemRect](../Topic/CHeaderCtrl::GetItemRect.md)|Recupera el rectángulo delimitador para un elemento determinado en un control de encabezado.|  
|[CHeaderCtrl::GetOrderArray](../Topic/CHeaderCtrl::GetOrderArray.md)|Recupera el orden de izquierda a derecha de elementos en un control de encabezado.|  
|[CHeaderCtrl::GetOverflowRect](../Topic/CHeaderCtrl::GetOverflowRect.md)|Obtiene el rectángulo delimitador del botón de desbordamiento para el control de encabezado actual.|  
|[CHeaderCtrl::HitTest](../Topic/CHeaderCtrl::HitTest.md)|Determina que el elemento de encabezado, si existe, se encuentra en un punto especificado.|  
|[CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md)|Inserta un nuevo elemento del control de encabezado.|  
|[CHeaderCtrl::Layout](../Topic/CHeaderCtrl::Layout.md)|Recupera el tamaño y la posición de un control de encabezado dentro de un rectángulo determinado.|  
|[CHeaderCtrl::OrderToIndex](../Topic/CHeaderCtrl::OrderToIndex.md)|Recupera el valor de índice de un elemento basándose en el orden en el control de encabezado.|  
|[CHeaderCtrl::SetBitmapMargin](../Topic/CHeaderCtrl::SetBitmapMargin.md)|Establece el ancho del margen de un mapa de bits en un control de encabezado.|  
|[CHeaderCtrl::SetFilterChangeTimeout](../Topic/CHeaderCtrl::SetFilterChangeTimeout.md)|Establece el intervalo de tiempo de espera entre el momento en que un cambio tiene lugar en los atributos de filtro y el envío de una notificación de `HDN_FILTERCHANGE` .|  
|[CHeaderCtrl::SetFocusedItem](../Topic/CHeaderCtrl::SetFocusedItem.md)|Establece el foco a un elemento especificado del encabezado del control de encabezado actual.|  
|[CHeaderCtrl::SetHotDivider](../Topic/CHeaderCtrl::SetHotDivider.md)|Cambia el divisor entre los elementos de encabezado para indicar un arrastrar y colocar manual de un elemento de encabezado.|  
|[CHeaderCtrl::SetImageList](../Topic/CHeaderCtrl::SetImageList.md)|Asigna una imagen orden a un control de encabezado.|  
|[CHeaderCtrl::SetItem](../Topic/CHeaderCtrl::SetItem.md)|Establece los atributos del elemento especificado en un control de encabezado.|  
|[CHeaderCtrl::SetOrderArray](../Topic/CHeaderCtrl::SetOrderArray.md)|Establece el orden de izquierda a derecha de elementos en un control de encabezado.|  
  
## Comentarios  
 Un control de encabezado es una ventana que se coloca normalmente en un conjunto de columnas de texto o los números.  Contiene un título para cada columna, y se puede dividir en elementos.  El usuario puede arrastrar divisores que separan las partes para establecer el ancho de cada columna.  Para obtener un ejemplo de un control de encabezado, vea [Controles de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775238).  
  
 Este control \(y por consiguiente la clase de `CHeaderCtrl` \) sólo está disponible para los programas que se ejecutan con una versión de Windows 3,51 95 \/98 y Windows NT y posterior.  
  
 La funcionalidad agregada para controles comunes de Windows 95 o Internet Explorer 4.0 incluye lo siguiente:  
  
-   El orden personalizado de elemento de encabezado.  
  
-   Arrastrar y colocar de elemento de encabezado, para reordenación de los elementos de encabezado.  Utilice el estilo de `HDS_DRAGDROP` cuando se crea el objeto de `CHeaderCtrl` .  
  
-   Texto de la columna de encabezado siempre visible durante el tamaño de la columna.  Utilice el estilo de `HDS_FULLDRAG` cuando se crea un objeto de `CHeaderCtrl` .  
  
-   Seguimiento activo de encabezado, que resalta el elemento de encabezado cuando el puntero se desplaza el mouse sobre él.  Utilice el estilo de `HDS_HOTTRACK` cuando se crea el objeto de `CHeaderCtrl` .  
  
-   Compatibilidad con la lista de imágenes.  Los elementos de encabezado pueden contener imágenes almacenadas en un objeto de `CImageList` o el texto.  
  
 Para obtener más información sobre cómo utilizar `CHeaderCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CHeaderCtrl](../../mfc/using-cheaderctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CTabCtrl Class](../../mfc/reference/ctabctrl-class.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)