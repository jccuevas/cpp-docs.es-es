---
title: CMFCDropDownFrame Clase
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
ms.openlocfilehash: 508b27acd0a2004b1b8f75fde0bddcdf91194948
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752429"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame Clase

Proporciona funcionalidad de ventana de marco desplegable a las barras de herramientas desplegables y a los botones de la barra de herramientas desplegables.

## <a name="syntax"></a>Sintaxis

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Miembros

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
|[CMFCDropDownFrame::Create](#create)|Crea un objeto `CMFCDropDownFrame` .|
|`CMFCDropDownFrame::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Recupera la barra de menús principal del marco desplegable.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Recupera el menú emergente principal del marco desplegable.|
|`CMFCDropDownFrame::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Reposiciona el marco desplegable.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Establece si la ventana de la barra de herramientas desplegable secundaria se destruye automáticamente.|

### <a name="remarks"></a>Observaciones

Esta clase no está pensada para utilizarla directamente desde el código.

El marco de trabajo usa esta `CMFCDropDownToolbar` `CMFCDropDownToolbarButton` clase para proporcionar el comportamiento de marco a las clases y. Para obtener más información acerca de estas clases, vea [CMFCDropDownToolBar (Clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md) y [CMFCDropDownToolbarButton (Clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCDropDownFrame` cómo recuperar `CFrameWnd` un puntero a un objeto de una clase y cómo establecer la ventana de la barra de herramientas desplegable secundaria para que se destruya automáticamente.

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

## <a name="cmfcdropdownframecreate"></a><a name="create"></a>CMFCDropDownFrame::Create

Crea un objeto `CMFCDropDownFrame` .

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
|*pWndParent*|[en] La ventana principal del marco desplegable.|
|*x*|[en] Coordenada de pantalla horizontal para la ubicación del marco descendente.|
|*y y*|[en] Coordenada de pantalla vertical para la ubicación del marco descendente.|
|*pWndOriginToolbar*|[en] La barra de herramientas que tiene los botones desplegables que este método utiliza para rellenar el nuevo objeto de marco desplegable.|

### <a name="return-value"></a>Valor devuelto

TRUESi el marco desplegable se creó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método llama a la base [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) método para crear la ventana de marco desplegable con el estilo de WS_POPUP. La ventana de marco desplegable aparece en las coordenadas de pantalla especificadas. Este método produce un error si el [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) método devuelve FALSE.

La `CMFCDropDownFrame` clase crea una `CMFCDropDownToolBar` copia del parámetro proporcionado. Este método copia las imágenes `pWndOriginToolbar` de `m_pWndOriginToolbar` botón y los estados de botón del parámetro al miembro de datos.

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

Recupera la barra de menús principal del marco desplegable.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la barra de menús principal del marco desplegable, o NULL si el marco no tiene ningún elemento primario.

### <a name="remarks"></a>Observaciones

Este método recupera la barra de menús principal del botón primario. Este método devuelve NULL si el marco desplegable no tiene ningún botón primario o el botón primario no tiene ninguna barra de menús primaria.

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Recupera el menú emergente principal del marco desplegable.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al menú desplegable primario del marco desplegable, o NULL si el marco no tiene ningún elemento primario.

### <a name="remarks"></a>Observaciones

Este método recupera el menú primario del botón primario. Este método devuelve NULL si el marco desplegable no tiene ningún botón primario o el botón primario no tiene ningún menú primario.

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout

Reposiciona el marco desplegable.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*bNotificar*|[in] Sin utilizar.|

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando se crea el marco desplegable o se cambia el tamaño de la ventana primaria. Este método calcula la posición y el tamaño del marco desplegable utilizando la posición y el tamaño de la ventana primaria.

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Establece si la ventana de la barra de herramientas desplegable secundaria se destruye automáticamente.

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoDestroy*<br/>
[en] TRUE para destruir automáticamente la ventana de la barra de herramientas desplegable asociada; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si *bAutoDestroy* es TRUE, el `CMFCDropDownFrame` destructor destruye la ventana de barra de herramientas desplegable asociada. El valor predeterminado es TRUE.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar (clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton (Clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
