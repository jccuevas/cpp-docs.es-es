---
title: Clase CMFCBaseToolBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseToolBar::CreateObject
- ~CMFCBaseToolBar
- CMFCBaseToolBar
- CMFCBaseToolBar::CMFCBaseToolBar
- CMFCBaseToolBar::~CMFCBaseToolBar
- CMFCBaseToolBar.~CMFCBaseToolBar
- CreateObject
- CMFCBaseToolBar.CMFCBaseToolBar
- CMFCBaseToolBar.CreateObject
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseToolBar class, constructor
- CMFCBaseToolBar class, destructor
- ~CMFCBaseToolBar destructor
- CreateObject method
- CMFCBaseToolBar class
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
caps.latest.revision: 19
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f608b23c0dbee3ec0e2d2b234612365e3c2461b0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbasetoolbar-class"></a>Clase CMFCBaseToolBar
Clase base para las barras de herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCBaseToolBar : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCBaseToolBar::CMFCBaseToolBar`|Constructor predeterminado.|  
|`CMFCBaseToolBar::~CMFCBaseToolBar`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCBaseToolBar::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento. (Invalida [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|  
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Devuelve el tamaño mínimo de una barra de herramientas. (Invalida [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Llamado por el marco después de realizar cambios del panel primario. (Invalida [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxbasetoolbar.h  
  
##  <a name="a-namegetdockingmodea--cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a>CMFCBaseToolBar::GetDockingMode  
 Devuelve el modo de acoplamiento.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de acoplamiento.  
  
##  <a name="a-namegetminsizea--cmfcbasetoolbargetminsize"></a><a name="getminsize"></a>CMFCBaseToolBar::GetMinSize  
 Devuelve el tamaño mínimo de una barra de herramientas.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 El tamaño mínimo de una barra de herramientas.  
  
##  <a name="a-nameonafterchangeparenta--cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a>CMFCBaseToolBar::OnAfterChangeParent  
 Llamado por el marco después de realizar cambios del panel primario.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndOldParent`  
 Puntero a la ventana primaria anterior.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

