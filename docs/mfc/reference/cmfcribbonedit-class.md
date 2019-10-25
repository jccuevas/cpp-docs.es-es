---
title: Clase CMFCRibbonEdit
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
ms.openlocfilehash: 4f973074fbec3d04b1c1a74852b02ff2564217c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504946"
---
# <a name="cmfcribbonedit-class"></a>Clase CMFCRibbonEdit

Implementa un control de edición que se encuentra en una barra de cinta.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indica si el alto del `CMFCRibbonEdit` control puede aumentar verticalmente hasta el alto de una fila de la cinta de opciones.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copia el estado del objeto especificado `CMFCRibbonEdit` en el objeto actual `CMFCRibbonEdit` .|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Crea un nuevo cuadro de texto para `CMFCRibbonEdit` el objeto.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Destruye el objeto `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Quita un cuadro de lista.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Habilita y establece el intervalo del botón de número para el cuadro de texto.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Recupera el tamaño compacto del `CFMCRibbonEdit` objeto.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Recupera el texto del cuadro de texto.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Recupera el tamaño intermedio del `CMFCRibbonEdit` objeto.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Recupera la alineación del texto en el cuadro de texto.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Recupera el ancho, en píxeles, del `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indica si el tamaño de `CMFCRibbonEdit` presentación del control puede ser compacto.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indica si el `CMFCRIbbonEdit` control tiene el foco.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indica si el tamaño de `CMFCRibbonEdit` presentación del control puede ser grande.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indica si el cuadro de texto tiene un botón de número.|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indica si el `CMFCRibbonEdit` control está resaltado.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Lo llama el marco de trabajo cuando cambian las dimensiones del rectángulo de `CMFCRibbonEdit` presentación para el control.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Lo llama el marco de trabajo para `CMFCRibbonEdit` dibujar el control.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Lo llama el marco de trabajo para dibujar la etiqueta y la `CMFCRibbonEdit` imagen para el control.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Lo llama el marco de trabajo para `CMFCRibbonEdit` dibujar el control en un cuadro de lista de comandos.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Lo llama el marco de trabajo para habilitar o `CMFCRibbonEdit` deshabilitar el control.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Lo llama el marco de trabajo cuando el puntero entra o sale de los límites `CMFCRibbonEdit` del control.|
|[CMFCRibbonEdit::OnKey](#onkey)|Lo llama el marco de trabajo cuando el usuario presiona un KeyTip `CMFCRibbonEdit` y el control tiene el foco.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Lo llama el marco de trabajo para `CMFCRibbonEdit` actualizar el control cuando el usuario presiona el botón primario del mouse en el control.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Lo llama el marco de trabajo cuando el usuario suelta el botón primario del mouse.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Lo llama el marco de trabajo para `CMFCRibbonEdit` actualizar el control cuando el diseño cambia de dirección.|
|[CMFCRibbonEdit::OnShow](#onshow)|Lo llama el marco de trabajo para mostrar u `CMFCRibbonEdit` ocultar el control.|
|[CMFCRibbonEdit::Redraw](#redraw)|Actualiza la presentación del `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Establece los datos de accesibilidad para `CMFCRibbonEdit` el objeto.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Establece el texto del cuadro de texto.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Establece la alineación del texto del cuadro de texto.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Establece el ancho del cuadro `CMFCRibbonEdit` de texto del control.|

## <a name="remarks"></a>Comentarios

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir `CMFCRibbonEdit` un objeto, Mostrar botones de número junto al control de edición y establecer el texto del control de edición. Este fragmento de código forma parte del [ejemplo de demostración de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonEdit. h

##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched

Indica si el alto del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) puede aumentar verticalmente hasta el alto de una fila de la cinta.

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit

Construye un objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
de Identificador de comando para `CMFCRibbonEdit` el control.

*nWidth*<br/>
de Ancho, en píxeles, del cuadro `CMFCRibbonEdit` de texto del control.

*lpszLabel*<br/>
de Etiqueta `CMFCRibbonEdit` del control.

*nImage*<br/>
de Índice de la imagen pequeña que se va a `CMFCRibbonEdit` usar para el control. La colección de imágenes pequeñas se mantiene en la categoría de la cinta de opciones primaria.

### <a name="remarks"></a>Comentarios

El `CMFCRibbonEdit` control no utiliza una imagen grande.

##  <a name="copyfrom"></a>CMFCRibbonEdit:: CopyFrom

Copia el estado del objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) especificado en el objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) actual.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
de Objeto de `CMFCRibbonEdit` origen.

### <a name="remarks"></a>Comentarios

El parámetro *src* debe ser de tipo `CMFCRibbonEdit`.

##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit

Crea un nuevo cuadro de texto para el objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la ventana primaria del `CMFCRibbonEdit` objeto.

*dwEditStyle*<br/>
de Especifica el estilo del cuadro de texto. Puede combinar los estilos de ventana que se muestran en la sección Comentarios con los [estilos de control de edición](/windows/win32/Controls/edit-control-styles) que se describen en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Puntero al nuevo cuadro de texto si el método se realizó correctamente; de lo contrario, es NULL.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para crear un cuadro de texto personalizado.

Puede aplicar los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un cuadro de texto:

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl

Destruye el objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Comentarios

##  <a name="dropdownlist"></a>CMFCRibbonEdit::D ropDownList

Quita un cuadro de lista.

```
virtual void DropDownList();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método no hace nada. Invalide este método para desplegar un cuadro de lista.

##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons

Habilita y establece el intervalo del botón de número para el cuadro de texto.

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
de Valor mínimo del botón de número.

*Nmáx.*<br/>
de Valor máximo del botón de número.

### <a name="remarks"></a>Comentarios

Los botones de número muestran una flecha hacia arriba y hacia abajo y permiten a los usuarios desplazarse por un conjunto fijo de valores.

##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize

Recupera el tamaño compacto del objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero a un contexto de dispositivo para `CMFCRibbonEdit` el objeto.

### <a name="return-value"></a>Valor devuelto

Tamaño compacto del `CMFCRibbonEdit` objeto.

### <a name="remarks"></a>Comentarios

##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText

Recupera el texto del cuadro de texto.

```
CString GetEditText() const;
```

### <a name="return-value"></a>Valor devuelto

Texto del cuadro de texto.

### <a name="remarks"></a>Comentarios

##  <a name="getintermediatesize"></a>  CMFCRibbonEdit::GetIntermediateSize

Recupera el tamaño intermedio del objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero a un contexto de dispositivo para `CMFCRibbonEdit` el objeto.

### <a name="return-value"></a>Valor devuelto

Tamaño intermedio del `CMFCRibbonEdit` objeto.

### <a name="remarks"></a>Comentarios

##  <a name="gettextalign"></a>  CMFCRibbonEdit::GetTextAlign

Recupera la alineación del texto en el cuadro de texto.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Valor devuelto

Valor enumerado de alineación de texto. Vea la sección Comentarios para ver los posibles valores.

### <a name="remarks"></a>Comentarios

El valor devuelto es uno de los siguientes estilos de control de edición:

- **ES_LEFT** para la alineación izquierda

- **ES_CENTER** para alineación central

- **ES_RIGHT** para la alineación derecha

Para obtener más información sobre estos estilos, vea [Editar estilos de control](/windows/win32/Controls/edit-control-styles).

##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth

Recupera el ancho, en píxeles, del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parámetros

*bInFloatyMode*<br/>
de True si el `CMFCRibbonEdit` control está en modo flotante; en caso contrario, false.

### <a name="return-value"></a>Valor devuelto

Ancho, en píxeles, del `CMFCRibbonEdit` control.

### <a name="remarks"></a>Comentarios

##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode

Indica si el tamaño de presentación del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) puede ser compacto.

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve TRUE. Invalide este método para indicar si el tamaño de presentación puede ser compacto.

##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus

Indica si el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) tiene el foco.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valor devuelto

True si el `CMFCRibbonEdit` control tiene el foco; en caso contrario, false.

### <a name="remarks"></a>Comentarios

##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode

Indica si el tamaño de presentación del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) puede ser grande.

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve FALSE. Invalide este método para indicar si el tamaño de presentación puede ser grande.

##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons

Indica si el cuadro de texto tiene un botón de número.

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro de texto tiene un botón de número; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="ishighlighted"></a>  CMFCRibbonEdit::IsHighlighted

Indica si el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) está resaltado.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valor devuelto

True si el `CMFCRibbonEdit` control está resaltado; de lo contrario, false.

### <a name="remarks"></a>Comentarios

##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect

Lo llama el marco de trabajo cuando cambian las dimensiones del rectángulo de presentación para el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero a un contexto de dispositivo para `CMFCRibbonEdit` el control.

### <a name="remarks"></a>Comentarios

##  <a name="ondraw"></a>CMFCRibbonEdit:: OnDraw

Lo llama el marco de trabajo para dibujar el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero a un contexto de dispositivo para `CMFCRibbonEdit` el control.

### <a name="remarks"></a>Comentarios

##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage

Lo llama el marco de trabajo para dibujar la etiqueta y la imagen para el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero a un contexto de dispositivo para `CMFCRibbonEdit` el control.

### <a name="remarks"></a>Comentarios

##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList

Lo llama el marco de trabajo para dibujar el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) en un cuadro de lista de comandos.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Puntero a un contexto de dispositivo para `CMFCRibbonEdit` el control.

*strText*<br/>
[in] El texto de presentación [](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit clase").

*nTextOffset*<br/>
de Distancia, en píxeles, desde el lado izquierdo del cuadro de lista hasta el texto para mostrar.

*rect*<br/>
de Rectángulo de `CMFCRibbonEdit` presentación del control.

*bIsSelected*<br/>
de Este parámetro no se utiliza.

*bHighlighted*<br/>
de Este parámetro no se utiliza.

### <a name="remarks"></a>Comentarios

El cuadro de lista comandos muestra los controles de la cinta de opciones para permitir que los usuarios personalicen la barra de herramientas de acceso rápido.

##  <a name="onenable"></a>CMFCRibbonEdit:: enable

Lo llama el marco de trabajo para habilitar o deshabilitar el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE para habilitar el control; FALSE para deshabilitar el control.

### <a name="remarks"></a>Comentarios

##  <a name="onhighlight"></a>CMFCRibbonEdit:: Resalte

Lo llama el marco de trabajo cuando el puntero entra o sale de los límites del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parámetros

*bHighlight*<br/>
de True si el puntero está en los límites del `CMFCRibbonEdit` control; en caso contrario, false.

### <a name="remarks"></a>Comentarios

##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey

Lo llama el marco de trabajo cuando el usuario presiona un KeyTip y el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) tiene el foco.

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parámetros

*bIsMenuKey*<br/>
de TRUE si KeyTip muestra un menú emergente; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si se controló el evento; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="onlbuttondown"></a>CMFCRibbonEdit:: OnLButtonDown

Lo llama el marco de trabajo para actualizar el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) cuando el usuario presiona el botón primario del mouse en el control.

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
de Este parámetro no se utiliza.

### <a name="remarks"></a>Comentarios

##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

Lo llama el marco de trabajo cuando el usuario suelta el botón primario del mouse.

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
de Este parámetro no se utiliza.

### <a name="remarks"></a>Comentarios

##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged

Lo llama el marco de trabajo para actualizar el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) cuando el diseño cambia de dirección.

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parámetros

*bIsRTL*<br/>
de TRUE si el diseño es de derecha a izquierda; FALSE si el diseño es de izquierda a derecha.

### <a name="remarks"></a>Comentarios

##  <a name="onshow"></a>CMFCRibbonEdit:: show

Lo llama el marco de trabajo para mostrar u ocultar el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
de TRUE para mostrar el control; FALSE para ocultar el control.

### <a name="remarks"></a>Comentarios

##  <a name="redraw"></a>CMFCRibbonEdit:: redraw

Actualiza la presentación del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void Redraw();
```

### <a name="remarks"></a>Comentarios

Este método vuelve a dibujar el rectángulo de `CMFCRibbonEdit` presentación del objeto mediante una llamada indirecta a [CWnd:: RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) con el conjunto de marcas RDW_INVALIDATE, RDW_ERASE y RDW_UPDATENOW.

##  <a name="setaccdata"></a>CMFCRibbonEdit:: SetACCData

Establece los datos de accesibilidad para el objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
Puntero a la ventana `CMFCRibbonEdit` primaria del objeto.

*data*<br/>
Los datos de accesibilidad para `CMFCRibbonEdit` el objeto.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText

Establece el texto del cuadro de texto.

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parámetros

*strText*<br/>
de Texto del cuadro de texto.

##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign

Establece la alineación del texto del cuadro de texto.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parámetros

*nAlign*<br/>
de Valor enumerado de alineación de texto. Vea la sección Comentarios para ver los posibles valores.

### <a name="remarks"></a>Comentarios

El parámetro *nAlign* es uno de los siguientes estilos de control de edición:

- ES_LEFT para la alineación izquierda

- ES_CENTER para alineación central

- ES_RIGHT para la alineación derecha

Para obtener más información sobre estos estilos, vea [Editar estilos de control](/windows/win32/Controls/edit-control-styles).

##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth

Establece el ancho del cuadro de texto para el control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
de Ancho, en píxeles, del cuadro de texto.

*bInFloatyMode*<br/>
TRUE para establecer el ancho del modo flotante; FALSE para establecer el ancho del modo normal.

### <a name="remarks"></a>Comentarios

El `CMFCRibbonEdit` control tiene dos anchos en función del modo de presentación: modo flotante y modo normal.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
