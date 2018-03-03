---
title: Clase CMFCBaseToolBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57a09465a342a74e69d199d725ec64e7c60ca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
##  <a name="getdockingmode"></a>CMFCBaseToolBar::GetDockingMode  
 Devuelve el modo de acoplamiento.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de acoplamiento.  
  
##  <a name="getminsize"></a>CMFCBaseToolBar::GetMinSize  
 Devuelve el tamaño mínimo de una barra de herramientas.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 El tamaño mínimo de una barra de herramientas.  
  
##  <a name="onafterchangeparent"></a>CMFCBaseToolBar::OnAfterChangeParent  
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
