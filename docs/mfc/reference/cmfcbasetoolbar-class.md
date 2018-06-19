---
title: Clase CMFCBaseToolBar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edc35091fef87c007fad73be45297536a170ca19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366322"
---
# <a name="cmfcbasetoolbar-class"></a>Clase CMFCBaseToolBar
Clase base para las barras de herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCBaseToolBar : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCBaseToolBar::CMFCBaseToolBar`|Constructor predeterminado.|  
|`CMFCBaseToolBar::~CMFCBaseToolBar`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCBaseToolBar::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento. (Invalida [cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|  
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Devuelve el tamaño mínimo de una barra de herramientas. (Invalida [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Lo llama el marco de trabajo después de realizar cambios de elemento primario del panel. (Invalida [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxbasetoolbar.h  
  
##  <a name="getdockingmode"></a>  CMFCBaseToolBar::GetDockingMode  
 Devuelve el modo de acoplamiento.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de acoplamiento.  
  
##  <a name="getminsize"></a>  CMFCBaseToolBar::GetMinSize  
 Devuelve el tamaño mínimo de una barra de herramientas.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 El tamaño mínimo de una barra de herramientas.  
  
##  <a name="onafterchangeparent"></a>  CMFCBaseToolBar::OnAfterChangeParent  
 Lo llama el marco de trabajo después de realizar cambios de elemento primario del panel.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndOldParent`  
 Un puntero a la ventana primaria anterior.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
