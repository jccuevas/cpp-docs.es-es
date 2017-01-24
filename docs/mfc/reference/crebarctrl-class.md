---
title: "CReBarCtrl Class | Microsoft Docs"
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
  - "CReBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBarCtrl class"
  - "rebar controls, control bar"
  - "rebar controls, CReBarCtrl class"
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CReBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula la funcionalidad de un control rebar, que es un contenedor para una ventana secundaria.  
  
## Sintaxis  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReBarCtrl::CReBarCtrl](../Topic/CReBarCtrl::CReBarCtrl.md)|Crea un objeto `CReBarCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReBarCtrl::BeginDrag](../Topic/CReBarCtrl::BeginDrag.md)|Coloca el control rebar en modo de arrastrar y colocar.|  
|[CReBarCtrl::Create](../Topic/CReBarCtrl::Create.md)|Crea el control rebar y lo asocia al objeto de `CReBarCtrl` .|  
|[CReBarCtrl::CreateEx](../Topic/CReBarCtrl::CreateEx.md)|Crea un control rebar con Windows especificado extendidas estilos y lo asocia a un objeto de `CReBarCtrl` .|  
|[CReBarCtrl::DeleteBand](../Topic/CReBarCtrl::DeleteBand.md)|Elimina una banda de un control rebar.|  
|[CReBarCtrl::DragMove](../Topic/CReBarCtrl::DragMove.md)|Actualiza la posición de arrastre en el control rebar después de una llamada a `BeginDrag`.|  
|[CReBarCtrl::EndDrag](../Topic/CReBarCtrl::EndDrag.md)|Finaliza la operación de arrastrar y colocar de control rebar.|  
|[CReBarCtrl::GetBandBorders](../Topic/CReBarCtrl::GetBandBorders.md)|Recupera los bordes de una banda.|  
|[CReBarCtrl::GetBandCount](../Topic/CReBarCtrl::GetBandCount.md)|Recupera el recuento de bandas actualmente en el control rebar.|  
|[CReBarCtrl::GetBandInfo](../Topic/CReBarCtrl::GetBandInfo.md)|Información de recupera sobre una banda especificada en un control rebar.|  
|[CReBarCtrl::GetBandMargins](../Topic/CReBarCtrl::GetBandMargins.md)|Recupera los márgenes de una banda.|  
|[CReBarCtrl::GetBarHeight](../Topic/CReBarCtrl::GetBarHeight.md)|Recupera el alto del control rebar.|  
|[CReBarCtrl::GetBarInfo](../Topic/CReBarCtrl::GetBarInfo.md)|La información de recupera sobre el control rebar y la imagen enumerarlo utiliza.|  
|[CReBarCtrl::GetBkColor](../Topic/CReBarCtrl::GetBkColor.md)|Recupera el color de fondo predeterminado de un control rebar.|  
|[CReBarCtrl::GetColorScheme](../Topic/CReBarCtrl::GetColorScheme.md)|Recupera la estructura de [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) asociada al control rebar.|  
|[CReBarCtrl::GetDropTarget](../Topic/CReBarCtrl::GetDropTarget.md)|Recupera el puntero de interfaz de `IDropTarget` de un control rebar.|  
|[CReBarCtrl::GetExtendedStyle](../Topic/CReBarCtrl::GetExtendedStyle.md)|Obtiene el estilo extendido del control actual rebar.|  
|[CReBarCtrl::GetImageList](../Topic/CReBarCtrl::GetImageList.md)|Recupera la lista de imágenes asociada a un control rebar.|  
|[CReBarCtrl::GetPalette](../Topic/CReBarCtrl::GetPalette.md)|Recupera la paleta actual del control rebar.|  
|[CReBarCtrl::GetRect](../Topic/CReBarCtrl::GetRect.md)|Recupera el rectángulo delimitador de una banda determinada en un control rebar.|  
|[CReBarCtrl::GetRowCount](../Topic/CReBarCtrl::GetRowCount.md)|Recupera el número de filas de la banda en un control rebar.|  
|[CReBarCtrl::GetRowHeight](../Topic/CReBarCtrl::GetRowHeight.md)|Recupera el alto de una fila especificada en un control rebar.|  
|[CReBarCtrl::GetTextColor](../Topic/CReBarCtrl::GetTextColor.md)|Recupera el color del texto predeterminado de un control rebar.|  
|[CReBarCtrl::GetToolTips](../Topic/CReBarCtrl::GetToolTips.md)|Recupera el identificador a cualquier control de información sobre herramientas asociada al control rebar.|  
|[CReBarCtrl::HitTest](../Topic/CReBarCtrl::HitTest.md)|Determina qué parte de una banda rebar es en un punto determinado de la pantalla, si existe una banda rebar en ese momento.|  
|[CReBarCtrl::IDToIndex](../Topic/CReBarCtrl::IDToIndex.md)|Convierte un identificador \(ID\) de banda a un índice de banda en un control rebar.|  
|[CReBarCtrl::InsertBand](../Topic/CReBarCtrl::InsertBand.md)|Inserta una nueva banda en un control rebar.|  
|[CReBarCtrl::MaximizeBand](../Topic/CReBarCtrl::MaximizeBand.md)|Cambia el tamaño de una banda en un control rebar al tamaño más grande.|  
|[CReBarCtrl::MinimizeBand](../Topic/CReBarCtrl::MinimizeBand.md)|Cambia el tamaño de una banda en un control rebar a su tamaño menor.|  
|[CReBarCtrl::MoveBand](../Topic/CReBarCtrl::MoveBand.md)|Mueve una banda a partir de un índice a otro.|  
|[CReBarCtrl::PushChevron](../Topic/CReBarCtrl::PushChevron.md)|Mediante programación inserta un botón de contenido adicional.|  
|[CReBarCtrl::RestoreBand](../Topic/CReBarCtrl::RestoreBand.md)|Cambia el tamaño de una banda en un control rebar a su tamaño ideal.|  
|[CReBarCtrl::SetBandInfo](../Topic/CReBarCtrl::SetBandInfo.md)|Establece características de una banda existente en un control rebar.|  
|[CReBarCtrl::SetBandWidth](../Topic/CReBarCtrl::SetBandWidth.md)|Establece el ancho de banda acoplada especificada en el control actual rebar.|  
|[CReBarCtrl::SetBarInfo](../Topic/CReBarCtrl::SetBarInfo.md)|Establece las características de un control rebar.|  
|[CReBarCtrl::SetBkColor](../Topic/CReBarCtrl::SetBkColor.md)|Establece el color de fondo predeterminado de un control rebar.|  
|[CReBarCtrl::SetColorScheme](../Topic/CReBarCtrl::SetColorScheme.md)|Establece la combinación de colores de los botones en un control rebar.|  
|[CReBarCtrl::SetExtendedStyle](../Topic/CReBarCtrl::SetExtendedStyle.md)|Establece los estilos extendidos para el control actual rebar.|  
|[CReBarCtrl::SetImageList](../Topic/CReBarCtrl::SetImageList.md)|Establece la lista de imágenes de un control rebar.|  
|[CReBarCtrl::SetOwner](../Topic/CReBarCtrl::SetOwner.md)|Establece la ventana propietaria de un control rebar.|  
|[CReBarCtrl::SetPalette](../Topic/CReBarCtrl::SetPalette.md)|Establece la paleta actual del control rebar.|  
|[CReBarCtrl::SetTextColor](../Topic/CReBarCtrl::SetTextColor.md)|Establece el color de texto predeterminado de un control rebar.|  
|[CReBarCtrl::SetToolTips](../Topic/CReBarCtrl::SetToolTips.md)|Asocia un control de información sobre herramientas al control rebar.|  
|[CReBarCtrl::SetWindowTheme](../Topic/CReBarCtrl::SetWindowTheme.md)|Establece el estilo visual del control rebar.|  
|[CReBarCtrl::ShowBand](../Topic/CReBarCtrl::ShowBand.md)|Muestra u oculta una banda determinada en un control rebar.|  
|[CReBarCtrl::SizeToRect](../Topic/CReBarCtrl::SizeToRect.md)|Llenan un control rebar un rectángulo especificado.|  
  
## Comentarios  
 La aplicación en la que el control rebar reside las asignaciones la ventana secundaria contiene junto al control rebar a la banda rebar.  La ventana secundaria normalmente es otro control común.  
  
 Los controles Rebar contienen una o más bandas.  Cada banda puede contener una combinación de una barra de agarrador, un mapa de bits, de una etiqueta de texto, y una ventana secundaria.  Banda puede contener solo uno de cada uno de estos elementos.  
  
 El control rebar puede mostrar la ventana secundaria sobre un mapa de bits de fondo especificado.  Todas las bandas de control rebar pueden cambiar el tamaño, excepto las que utilizan el estilo de **RBBS\_FIXEDSIZE** .  Cuando se coloca o cambia el tamaño de una banda de control de nuevo rebar, el control rebar controla el tamaño y la posición de la ventana secundaria asignada a la banda.  Para cambiar el tamaño o cambiar el orden de bandas dentro del control, haga clic y arrastre la barra del agarrador de una banda.  
  
 La ilustración siguiente se muestra un control rebar que tiene tres bandas:  
  
-   Banda 0 contiene un control toolbar plano, transparente.  
  
-   Banda 1 contiene el estándar transparente y botones desplegables transparentes.  
  
-   Banda 2 contiene un cuadro combinado y cuatro botones estándar.  
  
     ![Ejemplo de un menú Rebar](../../mfc/reference/media/vc4scc1.png "vc4SCC1")  
  
## Control Rebar  
 Compatibilidad de los controles Rebar:  
  
-   Listas de imágenes.  
  
-   Tráfico.  
  
-   Funcionalidad personalizada de dibujo.  
  
-   Una variedad de estilos de control además de estilos de ventana estándar.  Para obtener una lista de estos estilos, vea [Estilos de Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, vea [Mediante CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)