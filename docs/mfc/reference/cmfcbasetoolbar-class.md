---
title: CMFCBaseToolBar (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
ms.openlocfilehash: 027fe8569ff133bb3f348c9d0607f19c6d778c4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367829"
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar (Clase)

Clase base para barras de herramientas.

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
|`CMFCBaseToolBar::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento. (Reemplaza [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Devuelve el tamaño mínimo de una barra de herramientas. (Reemplaza [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Llamado por el marco de trabajo después de que cambie el elemento primario del panel. (Reemplaza [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbasetoolbar.h

## <a name="cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a>CMFCBaseToolBar::GetDockingMode

Devuelve el modo de acoplamiento.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Valor devuelto

El modo de acoplamiento.

## <a name="cmfcbasetoolbargetminsize"></a><a name="getminsize"></a>CMFCBaseToolBar::GetMinSize

Devuelve el tamaño mínimo de una barra de herramientas.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
[fuera] El tamaño mínimo de una barra de herramientas.

## <a name="cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a>CMFCBaseToolBar::OnAfterChangeParent

Llamado por el marco de trabajo después de que cambie el elemento primario del panel.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Parámetros

*pWndOldParent*<br/>
[en] Un puntero a la ventana primaria anterior.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
