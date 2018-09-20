---
title: CDockablePaneAdapter (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cec0a5c40d7937e8df20b5437b6dcc83b1b9ec1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441182"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter (clase)

Proporciona compatibilidad para paneles derivados de `CWnd`.

## <a name="syntax"></a>Sintaxis

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Devuelve la ventana ajustada.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Invalida [CDockablePane:: Loadstate](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter::SaveState](#savestate)|(Invalida [CDockablePane:: SaveState](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Comentarios

Normalmente, el marco de trabajo crea una instancia de objetos de esta clase cuando se usa el [cmfcbasetabctrl:: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) o [cmfcbasetabctrl:: insertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) métodos.

Si desea personalizar la `CDockablePaneAdapter` comportamiento, simplemente derivar una nueva clase y establezca la información de clase en tiempo de ejecución en una ventana con fichas mediante [cmfcbasetabctrl:: Setdockingbarwrapperrtc](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockablePaneAdapter.h

##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd

Devuelve la ventana subyacente para el adaptador de panel acoplable.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana ajustada.

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
[in] El nombre del perfil.

*nIndex*<br/>
[in] El índice del perfil.

*uiID*<br/>
[in] El identificador del panel.

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
[in] El nombre del perfil.

*nIndex*<br/>
[in] El índice de perfil (el valor predeterminado es el identificador de control de la ventana).

*uiID*<br/>
[in] El identificador del panel.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd

Establece la ventana subyacente para el adaptador de panel acoplable.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
[in] Un puntero a la ventana para ajustar el adaptador de panel.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)
