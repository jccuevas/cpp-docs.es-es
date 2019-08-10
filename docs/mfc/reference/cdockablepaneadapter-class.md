---
title: Clase CDockablePaneAdapter
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
ms.openlocfilehash: 88c125c63f9dbfe272f5d543e996366575fc533b
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866219"
---
# <a name="cdockablepaneadapter-class"></a>Clase CDockablePaneAdapter

Proporciona compatibilidad para paneles derivados de `CWnd`.

## <a name="syntax"></a>Sintaxis

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Devuelve la ventana ajustada.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Invalida [CDockablePane:: Loadstate](cdockablepane-class.md#loadstate)).|
|[CDockablePaneAdapter::SaveState](#savestate)|(Invalida [CDockablePane::](cdockablepane-class.md)SaveState).|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Comentarios

Normalmente, el marco de trabajo crea instancias de los objetos de esta clase cuando se usan los métodos [CMFCBaseTabCtrl:: AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) o [CMFCBaseTabCtrl:: insertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) .

Si desea personalizar el `CDockablePaneAdapter` comportamiento, simplemente derive una nueva clase a partir de ella y establezca la información de clase en tiempo de ejecución en una ventana con pestañas mediante [CMFCBaseTabCtrl:: SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[A cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockablePaneAdapter. h

##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd

Devuelve la ventana subyacente del adaptador del panel acoplable.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana ajustada.

### <a name="remarks"></a>Comentarios

Utilice esta función para tener acceso a la ventana ajustada.

##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState

Carga el estado del panel desde el registro.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Nombre del perfil.

*nIndex*<br/>
de Índice del perfil.

*uiID*<br/>
de IDENTIFICADOR del panel.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="savestate"></a>  CDockablePaneAdapter::SaveState

Guarda el estado del panel en el registro.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Nombre del perfil.

*nIndex*<br/>
de El índice de perfil (el valor predeterminado es el identificador de control de la ventana).

*uiID*<br/>
de IDENTIFICADOR del panel.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd

Establece la ventana subyacente para el adaptador del panel acoplable.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Puntero a la ventana del adaptador de panel que se va a ajustar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)
