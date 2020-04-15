---
title: Clase CAutoHideDockSite
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: 3a4593ac17f0af26517144edb7b01a9ca4203b1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352977"
---
# <a name="cautohidedocksite-class"></a>Clase CAutoHideDockSite

El `CAutoHideDockSite` extiende la [clase CDockSite](../../mfc/reference/cdocksite-class.md) para implementar paneles de acoplamiento de ocultación automática.

## <a name="syntax"></a>Sintaxis

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CAutoHideDockSite::CAutoHideDockSite`|Construye un objeto `CAutoHideDockSite`.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Indica si `CAutoHideDockSite` se muestra en el menú del panel.|
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Determina si un objeto de panel base se deriva de la [cMFCAutoHideBar (clase).](../../mfc/reference/cmfcautohidebar-class.md)|
|[CAutoHideDockSite::DockPane](#dockpane)|Acopla un `CAuotHideDockSite` panel a este objeto.|
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Recupera el tamaño del sitio de acoplamiento en coordenadas de pantalla.|
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Redibuja el panel `CAutoHideDockSite` en el con los márgenes globales y el espaciado de botones.|
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Establece el margen en el lado izquierdo de la barra de acoplamiento.|
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Establece el margen en el lado derecho de la barra de acoplamiento.|
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Llama a [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) `CAutoHideDockSite`para los objetos del archivo .|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|Nombre|Descripción|
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Define el tamaño del espacio entre las barras de herramientas y el borde de la barra de acoplamiento. Este espacio se mide desde el borde izquierdo o el borde superior, dependiendo de la alineación del espacio de acoplamiento.|

## <a name="remarks"></a>Observaciones

Cuando se llama a [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes) `CAutoHideDockSite` , el marco de trabajo crea automáticamente un objeto. En la mayoría de los casos, no debería tener que crear instancias ni utilizar esta clase directamente.

La barra de acoplamiento es el espacio entre el lado izquierdo del panel de acoplamiento y el lado izquierdo de la [clase CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CAutoHideDockSite` muestra `CMFCAutoHideBar` cómo recuperar un objeto de un objeto y cómo establecer los márgenes izquierdo y derecho de la barra de acoplamiento.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxautohidedocksite.h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane

Determina si un panel base es un [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objeto o derivado de `CMFCAutoHideBar`.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pBar*|[en] El panel base que prueba el marco de trabajo.|

### <a name="return-value"></a>Valor devuelto

TRUESi *pBar* se `CMFCAutoHideBar`deriva de ; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Si un objeto de panel `CMFCAutoHideBar`base se `CAutoHideDockSite`deriva de , puede contener un archivo .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a>CAutoHideDockSite::DockPane

Acopla un panel a este [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) objeto.

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWnd*|[en] El panel que el marco de trabajo acopla.|
|*dockMethod*|[en] Opciones de acoplamiento para el panel.|
|*lpRect*|[en] Rectángulo que especifica los límites del panel acoplado.|

### <a name="remarks"></a>Observaciones

La implementación predeterminada no utiliza el parámetro *dockMethod*, que se proporciona para su uso futuro.

Si *lpRect* es NULL, el marco de trabajo coloca el panel en la ubicación predeterminada en el sitio de acoplamiento. Si el sitio de acoplamiento es horizontal, la ubicación predeterminada se encuentra en el extremo izquierdo del sitio de acoplamiento. De lo contrario, la ubicación predeterminada se encuentra en la parte superior del sitio de acoplamiento.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect

Recupera el tamaño del sitio de acoplamiento en coordenadas de pantalla.

```
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*Rect*|[en] Una referencia a un rectángulo. El método almacena el tamaño del sitio de acoplamiento en este rectángulo.|

### <a name="remarks"></a>Observaciones

El rectángulo se ajusta para los márgenes de desplazamiento para que no se incluyan.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace

El tamaño del espacio entre los bordes de la [CAutoHideDockSite clase](../../mfc/reference/cautohidedocksite-class.md) y el [CMFCAutoHideBar clase](../../mfc/reference/cmfcautohidebar-class.md) objetos.

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Observaciones

Cuando `CMFCAutoHideBar` a está acoplado `CAutoHideDockSite`en un , no debe ocupar todo el sitio del muelle. Esta variable global controla el espacio adicional `CMFCAutoHideBar` entre el `CAutoHideDockSite` borde izquierdo o superior del borde y el borde correspondiente. Si se utiliza el borde superior o izquierdo depende de la alineación actual.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft

Establece el margen en el lado izquierdo de la barra de acoplamiento.

```
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Parámetros

*nOffset*<br/>
[en] El nuevo desplazamiento.

### <a name="remarks"></a>Observaciones

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objetos se colocan estáticamente en el `CAutoHideDockSite` objeto. Esto significa que el usuario no `CMFCAutoHideBar` puede cambiar manualmente la ubicación de los objetos. El `SetOffsetLeft` método controla el espaciado entre el `CMFCAutoHideBar` lado izquierdo de `CAutoHideDockSite`la parte izquierda y el lado izquierdo del archivo .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight

Establece el margen en el lado derecho de la barra de acoplamiento.

```
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Parámetros

*nOffset*<br/>
[en] El nuevo desplazamiento.

### <a name="remarks"></a>Observaciones

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objetos se colocan estáticamente en el `CAutoHideDockSite` objeto. Esto significa que el usuario no puede `CMFCAutoHideBar` cambiar manualmente la ubicación de los objetos. El `SetOffsetRight` método controla el espaciado entre el `CMFCAutoHideBar` lado derecho de `CAutoHideDockSite`la parte derecha y el lado derecho del archivo .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes

Redibuja los paneles en [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*rectNewClientArea*|[en] Un valor reservado.|

### <a name="remarks"></a>Observaciones

La implementación predeterminada no utiliza *rectNewClientArea*. Redibuja los paneles con los márgenes de la barra de herramientas global y el espaciado de botones.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode

Llama a [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) para objetos en el sitio de acoplamiento.

```
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pAutoHideToolbar*|[en] Puntero a un panel de [objetos CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) ubicado en el `CAutoHideDockSite`archivo .|

### <a name="remarks"></a>Observaciones

Este método busca la fila que contiene *pAutoHideToolbar*. Llama `CMFCAutoHideBar.UnSetAutoHideMode` a todos `CMFCAutoHideBar` los objetos de esa fila. Si *pAutoHideToolbar* no se encuentra o es `CMFCAutoHideBar.UnSetAutoHideMode` NULL, `CMFCAutoHideBar` este `CAutoHideDockSite`método llama a todos los objetos del archivo .

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite Class](../../mfc/reference/cdocksite-class.md)
