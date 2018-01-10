---
title: Clase de COleIPFrameWnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs: C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1833cbbbfb6706cffe73770bcd9b61ff755a645
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="coleipframewnd-class"></a>Clase de COleIPFrameWnd
Base para la ventana de la edición en contexto de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Construye un objeto `COleIPFrameWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Llamado por el marco de trabajo cuando se activa un elemento para su edición en contexto.|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Lo llama el marco de trabajo para cambiar la posición de la ventana de edición en contexto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase crea y posiciones de las barras en la ventana de documento de la aplicación contenedora de control. También controla las notificaciones generadas por una incrustado [COleResizeBar](../../mfc/reference/coleresizebar-class.md) cuando el usuario cambia el tamaño de la ventana de edición en contexto del objeto.  
  
 Para obtener más información sobre el uso de `COleIPFrameWnd`, vea el artículo [activación](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd  
 Construye un `COleIPFrameWnd` objeto e inicializa la información de estado de en contexto, que se almacena en una estructura de tipo **OLEINPLACEFRAMEINFO**.  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) en el SDK de Windows.  
  
##  <a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars  
 Las llamadas de framework la `OnCreateControlBars` funcionar cuando se activa un elemento para su edición en contexto.  
  
```  
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,  
    CWnd* pWndDoc);

 
virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,  
    CFrameWnd* pWndDoc);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWndFrame*  
 Puntero a la ventana de marco de la aplicación contenedora.  
  
 *pWndDoc*  
 Puntero a la ventana de nivel de documento del contenedor. Puede ser **NULL** si el contenedor es una aplicación SDI.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ejecuta correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Reemplace esta función para realizar cualquier procesamiento especial necesario cuando se crean barras de control.  
  
##  <a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame  
 Las llamadas de framework la `RepositionFrame` función de miembro para diseñar barras de control y la posición de la ventana de edición en contexto para que sea visible completamente.  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPosRect`  
 Puntero a un `RECT` estructura o un `CRect` coordenadas de posición actual de la ventana, en píxeles, respecto al área de cliente de marco de objeto que contiene el contexto.  
  
 `lpClipRect`  
 Puntero a un `RECT` estructura o un `CRect` coordenadas del rectángulo de recorte actual de la ventana, en píxeles, respecto al área de cliente de marco de objeto que contiene el contexto.  
  
### <a name="remarks"></a>Comentarios  
 Diseño de las barras de control en la ventana contenedora de difiere del que realiza una ventana de marco no son compatibles con OLE. La ventana de marco no OLE calcula las posiciones de barras de controles y otros objetos de un tamaño de ventana de marco determinada, como en una llamada a [RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). El área de cliente es lo que permanece después de que se va a restar espacio para las barras de controles y otros objetos. Un `COleIPFrameWnd` ventana, coloca en otra parte, las barras de herramientas con arreglo a un área de cliente determinado. En otras palabras, `CFrameWnd::RecalcLayout` funciona "desde el exterior,", mientras que `COleIPFrameWnd::RepositionFrame` funciona "desde dentro hacia fuera."  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)
