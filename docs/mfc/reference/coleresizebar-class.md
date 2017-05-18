---
title: Clase COleResizeBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- OLE items, resizing
- in-place items
- in-place items, resizing
- resizing in-place OLE items
- control bars, resizing
- COleResizeBar class
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 99ba53c771d018b8c69c5951703b9d6f7b4afe9b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="coleresizebar-class"></a>Clase COleResizeBar
Un tipo de barra de control que admite el cambio de tamaño de elementos de OLE en contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](#coleresizebar)|Construye un objeto `COleResizeBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleResizeBar::Create](#create)|Crea, inicializa una ventana secundaria de Windows y lo asocia a la `COleResizeBar` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `COleResizeBar`los objetos aparecen como un [CRectTracker](../../mfc/reference/crecttracker-class.md) controladores de tamaño con un borde sombreado y externa.  
  
 `COleResizeBar`los objetos son normalmente incrustados miembros de objetos de ventana de marco derivada de la [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) clase.  
  
 Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coleresizebar"></a>COleResizeBar::COleResizeBar  
 Construye un objeto `COleResizeBar`.  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a **crear** para crear el objeto de la barra de cambio de tamaño.  
  
##  <a name="create"></a>COleResizeBar::Create  
 Crea una ventana secundaria y lo asocia a la `COleResizeBar` objeto.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la ventana primaria de la barra de cambio de tamaño.  
  
 `dwStyle`  
 Especifica la [estilo de ventana](../../mfc/reference/window-styles.md) atributos.  
  
 `nID`  
 Identificador de ventana secundaria de la barra de cambio de tamaño.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se creó la barra de cambio de tamaño; en caso contrario, 0.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC SUPERPAD](../../visual-cpp-samples.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

