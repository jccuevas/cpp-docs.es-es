---
title: CDockablePaneAdapter (clase)
ms.date: 11/04/2016
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
ms.openlocfilehash: 2fbaf99e4cc9bcbecf1a94012713b34e986f7ecb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375593"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter (clase)

Proporciona compatibilidad para paneles derivados de `CWnd`.

## <a name="syntax"></a>Sintaxis

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Devuelve la ventana ajustada.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Reemplaza [CDockablePane::LoadState](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter::SaveState](#savestate)|(Reemplaza [CDockablePane::SaveState](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Observaciones

Normalmente, el marco de trabajo crea instancias de objetos de esta clase cuando se utiliza el [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) o [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) métodos.

Si desea personalizar `CDockablePaneAdapter` el comportamiento, simplemente derive una nueva clase de él y establezca la información de la clase en tiempo de ejecución en una ventana con fichas mediante [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Cobject](../../mfc/reference/cobject-class.md)\
.&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockablePaneAdapter.h

## <a name="cdockablepaneadaptergetwrappedwnd"></a><a name="getwrappedwnd"></a>CDockablePaneAdapter::GetWrappedWnd

Devuelve la ventana subyacente para el adaptador de panel acoplable.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana ajustada.

### <a name="remarks"></a>Observaciones

Utilice esta función para acceder a la ventana ajustada.

## <a name="cdockablepaneadapterloadstate"></a><a name="loadstate"></a>CDockablePaneAdapter::LoadState

Carga el estado del panel desde el registro.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] El nombre del perfil.

*nIndex*<br/>
[en] El índice de perfil.

*uiID*<br/>
[en] El identificador del panel.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdockablepaneadaptersavestate"></a><a name="savestate"></a>CDockablePaneAdapter::SaveState

Guarda el estado del panel en el registro.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] El nombre del perfil.

*nIndex*<br/>
[en] El índice de perfil (valor predeterminado es el identificador de control de la ventana).

*uiID*<br/>
[en] El identificador del panel.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdockablepaneadaptersetwrappedwnd"></a><a name="setwrappedwnd"></a>CDockablePaneAdapter::SetWrappedWnd

Establece la ventana subyacente para el adaptador de panel acoplable.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[en] Un puntero a la ventana para el adaptador de panel para ajustar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
