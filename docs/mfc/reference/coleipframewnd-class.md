---
title: COleIPFrameWnd (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ceba9da99585cb9a88b5fa7fa43d10c9fe02836
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218804"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd (clase)
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
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Lo llama el marco de trabajo cuando se activa un elemento para su edición en contexto.|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Lo llama el marco de trabajo para volver a colocar la ventana de edición en contexto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase crea y las barras en la ventana de documento de la aplicación de contenedor de control de las posiciones. También controla las notificaciones generadas por incrustada [COleResizeBar](../../mfc/reference/coleresizebar-class.md) objeto cuando el usuario cambia el tamaño de la ventana de edición en contexto.  
  
 Para obtener más información sobre el uso de `COleIPFrameWnd`, consulte el artículo [activación](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd  
 Construye un `COleIPFrameWnd` objeto e inicializa su información de estado local, que se almacena en una estructura de tipo OLEINPLACEFRAMEINFO.  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [OLEINPLACEFRAMEINFO](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) en el SDK de Windows.  
  
##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars  
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
 Puntero a la ventana de nivel de documento del contenedor. Puede ser NULL si el contenedor es una aplicación SDI.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ejecuta correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Reemplace esta función para llevar a cabo ningún procesamiento especial necesario cuando se crean barras de control.  
  
##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame  
 Las llamadas de framework la `RepositionFrame` función miembro para diseñar barras de control y la posición de la ventana de edición en contexto para que todo esté visible.  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpPosRect*  
 Puntero a un `RECT` estructura o un `CRect` coordenadas de posición actual de la ventana, en píxeles, relativo al área cliente de marco que contiene el contexto del objeto.  
  
 *lpClipRect*  
 Puntero a un `RECT` estructura o un `CRect` coordenadas del rectángulo de recorte actual de la ventana, en píxeles, relativo al área cliente de marco que contiene el contexto del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Difiere de diseño de las barras de control en la ventana del contenedor que realiza mediante una ventana de marco que no son compatibles con OLE. La ventana de marco que no son compatibles con OLE calcula las posiciones de las barras de control y otros objetos de un tamaño de ventana de marco determinado, como se muestra en una llamada a [RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). El área de cliente es lo que queda después de que se resta espacio para las barras de control y otros objetos. Un `COleIPFrameWnd` ventana, por otro lado, coloca las barras de herramientas con arreglo a un área de cliente determinado. En otras palabras, `CFrameWnd::RecalcLayout` funciona "desde el exterior," mientras que `COleIPFrameWnd::RepositionFrame` funciona "desde dentro hacia fuera."  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)
