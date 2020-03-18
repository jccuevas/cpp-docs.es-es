---
title: Clase CMFCDropDownFrame
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: 534dc90443371c8440e0cb317540f2cf80f6eacc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425836"
---
# <a name="cmfcdropdownframe-class"></a>Clase CMFCDropDownFrame

Proporciona la funcionalidad de la ventana de marco desplegable para las barras de herramientas desplegables y los botones de la barra de herramientas desplegable.

## <a name="syntax"></a>Sintaxis

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Constructor predeterminado.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCDropDownFrame:: Create](#create)|Crea un objeto `CMFCDropDownFrame`.|
|`CMFCDropDownFrame::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Recupera la barra de menús primaria del marco desplegable.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Recupera el menú emergente primario del marco desplegable.|
|`CMFCDropDownFrame::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Cambia la posición del marco desplegable.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Establece si la ventana secundaria de la barra de herramientas desplegable se destruye automáticamente.|

### <a name="remarks"></a>Observaciones

Esta clase no está pensada para utilizarla directamente desde el código.

El marco de trabajo utiliza esta clase para proporcionar el comportamiento del marco a las clases `CMFCDropDownToolbar` y `CMFCDropDownToolbarButton`. Para obtener más información sobre estas clases, consulte [clase CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) y [clase CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo recuperar un puntero a un objeto `CMFCDropDownFrame` de una clase `CFrameWnd` y cómo establecer la ventana secundaria de la barra de herramientas desplegable que se va a destruir automáticamente.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdropdowntoolbar.h

##  <a name="create"></a>CMFCDropDownFrame:: Create

Crea un objeto `CMFCDropDownFrame`.

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWndParent*|de Ventana primaria del marco desplegable.|
|*x*|de La coordenada horizontal de la pantalla para la ubicación del marco de abajo.|
|*y*|de La coordenada vertical de la pantalla para la ubicación del marco de abajo.|
|*pWndOriginToolbar*|de Barra de herramientas que tiene los botones desplegables que usa este método para rellenar el nuevo objeto de marco desplegable.|

### <a name="return-value"></a>Valor devuelto

TRUE si el marco desplegable se ha creado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método llama al método base [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) para crear la ventana de marco desplegable con el estilo de WS_POPUP. La ventana de marco desplegable aparece en las coordenadas de pantalla especificadas. Este método produce un error si el método [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) devuelve false.

La clase `CMFCDropDownFrame` crea una copia del parámetro `CMFCDropDownToolBar` proporcionado. Este método copia las imágenes del botón y los Estados de los botones del parámetro `pWndOriginToolbar` al miembro de datos `m_pWndOriginToolbar`.

##  <a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

Recupera la barra de menús primaria del marco desplegable.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la barra de menús primaria del marco desplegable o NULL si el marco no tiene ningún elemento primario.

### <a name="remarks"></a>Observaciones

Este método recupera la barra de menús primaria del botón primario. Este método devuelve NULL si el marco desplegable no tiene ningún botón primario o el botón primario no tiene barra de menús primaria.

##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Recupera el menú emergente primario del marco desplegable.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al menú desplegable primario del marco desplegable o NULL si el marco no tiene ningún elemento primario.

### <a name="remarks"></a>Observaciones

Este método recupera el menú primario del botón primario. Este método devuelve NULL si el marco desplegable no tiene un botón primario o el botón primario no tiene ningún menú primario.

##  <a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout

Cambia la posición del marco desplegable.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*bNotify*|[in] Sin utilizar.|

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando se crea el marco desplegable o se cambia el tamaño de la ventana primaria. Este método calcula la posición y el tamaño del marco desplegable con la posición y el tamaño de la ventana primaria.

##  <a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Establece si la ventana secundaria de la barra de herramientas desplegable se destruye automáticamente.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoDestroy*<br/>
de TRUE para destruir automáticamente la ventana de la barra de herramientas desplegable asociada; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si *bAutoDestroy* es true, el destructor `CMFCDropDownFrame` destruye la ventana de la barra de herramientas desplegable asociada. El valor predeterminado es TRUE.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar (clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton (clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
