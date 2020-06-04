---
title: CMFCAutoHideButton (clase)
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 3ea6ce13b8cca7e0130fe14459a832b476391b0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751675"
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton (clase)

Botón que muestra u oculta una [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) configurada para ocultar.

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)| Crea e inicializa el botón de ocultación automática.|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Recupera la alineación del botón de ocultación automática.|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Devuelve el [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto asociado con el botón de ocultación automática.|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|Determina el tamaño del botón de ocultación automática.|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Devuelve el tamaño de la etiqueta de texto para el botón de ocultación automática.|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Resalta el botón de ocultación automática.|
|[CMFCAutoHideButton::IsActive](#isactive)|Indica si el botón de ocultación automática está activo.|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Devuelve el estado de resaltado del botón de ocultación automática.|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Determina si el botón de ocultación automática es horizontal o vertical.|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|Indica si el botón está visible.|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|El marco de trabajo llama a este método cuando dibuja el botón de ocultación automática.|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|El marco de trabajo llama a este método cuando dibuja el borde de un botón de ocultación automática.|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|El marco de trabajo llama a este método cuando rellena el fondo de un botón de ocultación automática.|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Muestra u oculta la [clase CDockablePane](../../mfc/reference/cdockablepane-class.md)asociada.|
|[CMFCAutoHideButton::ShowButton](#showbutton)|Muestra u oculta el botón de ocultación automática.|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Observaciones

En la `CMFCAutoHideButton` creación, el objeto se adjunta a una [clase CDockablePane](../../mfc/reference/cdockablepane-class.md). El objeto `CDockablePane` se oculta o se muestra cuando el usuario interactúa con el objeto `CMFCAutoHideButton`.

De forma predeterminada, el marco de trabajo crea automáticamente un `CMFCAutoHideButton` cuando el usuario activa la ocultación automática. El marco de trabajo puede crear un elemento de una clase de interfaz de usuario personalizada en lugar de la clase `CMFCAutoHideButton`. Para especificar qué clase de interfaz de usuario personalizada debería utilizar, establezca la variable de miembro estático `CMFCAutoHideBar::m_pAutoHideButtonRTS` igual que la clase de interfaz de usuario personalizada. De forma predeterminada, esta variable se establece en `CMFCAutoHideButton`.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo construir un objeto `CMFCAutoHideButton` y cómo usar varios métodos de la clase `CMFCAutoHideButton`. En el ejemplo se muestra cómo inicializar un objeto `CMFCAutoHideButton` mediante su método `Create`, mostrar la clase asociada `CDockablePane` y mostrar el botón de ocultación automática.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a>CMFCAutoHideButton::BringToTop

```cpp
void BringToTop();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a>CMFCAutoHideButton::Create

Crea e inicializa un botón de ocultación automática.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parámetros

*pParentBar*<br/>
[en] Un puntero a la barra de herramientas principal.

*pAutoHideWnd*<br/>
[en] Un puntero a un [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto. Este botón de ocultación `CDockablePane`automática oculta y muestra que .

*dwAlignment*<br/>
[en] Valor que especifica la alineación del botón con la ventana de marco principal.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Al crear `CMFCAutoHideButton` un objeto, debe asociar el botón `CDockablePane`de ocultación automática a un archivo . El usuario puede utilizar el botón de `CDockablePane`ocultación automática para ocultar y mostrar el archivo .

El parámetro *dwAlignment* indica dónde reside el botón de ocultación automática en la aplicación. El parámetro puede establecerse en uno de los valores siguientes:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a>CMFCAutoHideButton::GetAlignment

Recupera la alineación del botón de ocultación automática.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene la alineación actual del botón de ocultación automática.

### <a name="remarks"></a>Observaciones

La alineación del botón de ocultación automática indica dónde reside el botón en la aplicación. Puede ser cualquiera de los siguientes valores:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a>CMFCAutoHideButton::GetAutoHideWindow

Devuelve el [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto asociado con el botón de ocultación automática.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al `CDockablePane` objeto asociado.

### <a name="remarks"></a>Observaciones

Para asociar un botón `CDockablePane`de ocultación automática con un , pase el `CDockablePane` como un parámetro a la [CMFCAutoHideButton::Create](#create) método.

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFCAutoHideButton::GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a>CMFCAutoHideButton::GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a>CMFCAutoHideButton::GetSize

Determina el tamaño del botón de ocultación automática.

```
CSize GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `CSize` que contiene el tamaño del botón.

### <a name="remarks"></a>Observaciones

El tamaño calculado incluye el tamaño del borde del botón de ocultación automática.

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a>CMFCAutoHideButton::GetTextSize

Devuelve el tamaño de la etiqueta de texto para el botón de ocultación automática.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el tamaño del texto para el botón de ocultación automática.

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a>CMFCAutoHideButton::IsActive

Indica si el botón de ocultación automática está activo.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el botón de ocultación automática está activo; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Un botón de ocultación automática está activo cuando se muestra la ventana [de clase CDockablePane](../../mfc/reference/cdockablepane-class.md) asociada.

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a>CMFCAutoHideButton::IsHorizontal

Determina si el botón de ocultación automática es horizontal o vertical.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón es horizontal; 0 en caso contrario.

### <a name="remarks"></a>Observaciones

El marco de trabajo establece la orientación de un [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) objeto al crearlo.  Puede controlar la orientación mediante el *dwAlignment* parámetro en el [CMFCAutoHideButton::Create](#create) método.

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a>CMFCAutoHideButton::IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a>CMFCAutoHideButton::IsVisible

Indica si el botón de ocultación automática está visible.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el botón está visible; FALSE en caso contrario.

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a>CMFCAutoHideButton::OnDraw

El marco de trabajo llama a este método cuando dibuja el botón de ocultación automática.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

### <a name="remarks"></a>Observaciones

Si desea personalizar la apariencia de los botones de ocultación automática `CMFCAutoHideButton`en la aplicación, cree una nueva clase derivada de . En la clase derivada, invalide este método.

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a>CMFCAutoHideButton::OnDrawBorder

El marco de trabajo llama a este método cuando dibuja el borde de un botón de ocultación automática.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*rectBounds*<br/>
[en] El rectángulo delimitador del botón de ocultación automática.

*rectBorderSize*<br/>
[en] El grosor del borde para cada lado del botón de ocultación automática.

### <a name="remarks"></a>Observaciones

Si desea personalizar el borde de cada botón de ocultación automática en `CMFCAutoHideButton`la aplicación, cree una nueva clase derivada del archivo . En la clase derivada, invalide este método.

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a>CMFCAutoHideButton::OnFillBackground

El marco de trabajo llama a este método cuando rellena el fondo de un botón de ocultación automática.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] El rectángulo delimitador del botón de ocultación automática.

### <a name="remarks"></a>Observaciones

Si desea personalizar el fondo para ocultar automáticamente los botones de la `CMFCAutoHideButton`aplicación, cree una nueva clase derivada del archivo . En la clase derivada, invalide este método.

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a>CMFCAutoHideButton::ShowAttachedWindow

Muestra u oculta la [clase CDockablePane](../../mfc/reference/cdockablepane-class.md)asociada.

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[en] Un valor booleano que especifica `CDockablePane`si este método muestra el archivo .

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a>CMFCAutoHideButton::ShowButton

Muestra u oculta el botón de ocultación automática.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[en] Un valor booleano que especifica si se debe mostrar el botón de ocultación automática.

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a>CMFCAutoHideButton::Move

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>Parámetros

[en] *nOffset*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a>CMFCAutoHideButton::ReplacePane

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parámetros

[en] *pNewBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideButton::UnSetAutoHideMode

Permite deshabilitar el modo de ocultación automática.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>Parámetros

*pFirstBarInGroup*<br/>
[en] Un puntero a la primera barra del grupo.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a>CMFCAutoHideButton::HighlightButton

Resalta el botón de ocultación automática.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>Parámetros

*bResaltar*<br/>
Especifica el nuevo estado del botón de ocultación automática. TRUE indica que el botón está resaltado, FALSE indica que el botón no está resaltado.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a>CMFCAutoHideButton::IsHighlighted

Devuelve el estado de resaltado del botón de ocultación automática.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se resalta el botón de ocultación automática; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar (clase)](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[Clase CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)
