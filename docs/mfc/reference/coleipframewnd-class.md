---
title: Clase de COleIPFrameWnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd class
- OLE, editing
- OLE, in-place activation
- in-place editing
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 85ce028bb5d72c06a0e228abba1bd08a7f6526cb
ms.lasthandoff: 02/24/2017

---
# <a name="coleipframewnd-class"></a>Clase de COleIPFrameWnd
Base para la ventana de la edición en contexto de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Construye un objeto `COleIPFrameWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Llamado por el marco de trabajo cuando se activa un elemento para su edición en contexto.|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Llamado por el marco de trabajo para cambiar la posición de la ventana de edición en contexto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase crea y posiciones controlan barras dentro de la ventana de documento de la aplicación contenedora. También controla las notificaciones generadas por incrustado [COleResizeBar](../../mfc/reference/coleresizebar-class.md) objeto cuando el usuario cambia el tamaño de la ventana de edición en contexto.  
  
 Para obtener más información sobre el uso de `COleIPFrameWnd`, vea el artículo [activación](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="a-namecoleipframewnda--coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd  
 Construye un `COleIPFrameWnd` objeto e inicializa su información de estado de in situ, que se almacena en una estructura de tipo **OLEINPLACEFRAMEINFO**.  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameoncreatecontrolbarsa--coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars  
 El marco llama el `OnCreateControlBars` funciona cuando se activa un elemento para su edición en contexto.  
  
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
 Es distinto de cero en caso de éxito; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Reemplazar esta función para realizar cualquier procesamiento especial necesario cuando se crean barras de control.  
  
##  <a name="a-namerepositionframea--coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame  
 El marco llama el `RepositionFrame` función miembro para diseñar barras de control y cambiar la posición de la ventana de edición en contexto para que todo sea visible.  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPosRect`  
 Puntero a un `RECT` estructura o un `CRect` coordenadas de posición actual de la ventana, en píxeles, relativo al área cliente de marco que contiene el contexto del objeto.  
  
 `lpClipRect`  
 Puntero a un `RECT` estructura o un `CRect` coordenadas de rectángulo de recorte actual de la ventana, en píxeles, relativo al área cliente de marco que contiene el contexto del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Diseño de las barras de control en la ventana contenedora difiere realizadas por una ventana de marco no OLE. La ventana de marco no OLE calcula las posiciones de las barras de controles y otros objetos de un tamaño de ventana de marco determinado, como en una llamada a [RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). El área de cliente es lo que permanece después de resta el espacio para las barras de controles y otros objetos. Un `COleIPFrameWnd` ventana, por otro lado, coloca las barras de herramientas con arreglo a un área de cliente determinado. En otras palabras, `CFrameWnd::RecalcLayout` funciona "desde el exterior," mientras que `COleIPFrameWnd::RepositionFrame` funciona "desde dentro hacia fuera."  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)

