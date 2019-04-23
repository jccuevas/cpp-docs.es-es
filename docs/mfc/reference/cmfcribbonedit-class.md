---
title: CMFCRibbonEdit (clase)
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
ms.openlocfilehash: 80ee43ae32416f9f62df419c4afbd46a0aa63cc8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780488"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit (clase)

Implementa un control de edición que se encuentra en una barra de cinta.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indica si el alto de la `CMFCRibbonEdit` control puede aumentar verticalmente para el alto de una fila de la cinta de opciones.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copia el estado del elemento especificado `CMFCRibbonEdit` el objeto actual `CMFCRibbonEdit` objeto.|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Crea un nuevo cuadro de texto para el `CMFCRibbonEdit` objeto.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Destruye el objeto `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Despliega un cuadro de lista.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Habilita y configura el intervalo del botón de número para el cuadro de texto.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Recupera el tamaño compacto de la `CFMCRibbonEdit` objeto.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Recupera el texto en el cuadro de texto.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Recupera el tamaño intermedio de la `CMFCRibbonEdit` objeto.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Recupera la alineación del texto en el cuadro de texto.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Recupera el ancho, en píxeles, de la `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indica si la presentación de tamaño para el `CMFCRibbonEdit` control puede ser compacto.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indica si el `CMFCRIbbonEdit` control tiene el foco.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indica si la presentación de tamaño para el `CMFCRibbonEdit` control puede ser grande.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indica si el cuadro de texto tiene un botón de número.|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indica si el `CMFCRibbonEdit` control aparece resaltado.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Lo llama el marco cuando las dimensiones del rectángulo de presentación para el `CMFCRibbonEdit` controlar los cambios.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar el `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Lo llama el marco de trabajo para dibujar la etiqueta de imagen para el `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Lo llama el marco de trabajo para dibujar el `CMFCRibbonEdit` control en un cuadro de lista de comandos.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Lo llama el marco para habilitar o deshabilitar el `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Lo llama el marco cuando el puntero entra o sale de los límites del `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::OnKey](#onkey)|Lo llama el marco cuando el usuario presiona un keytip y `CMFCRibbonEdit` control tiene el foco.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Lo llama el marco de trabajo para actualizar el `CMFCRibbonEdit` controlar cuando el usuario presiona el botón primario del mouse en el control.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Lo llama el marco cuando el usuario suelta el botón primario del mouse.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Lo llama el marco de trabajo para actualizar el `CMFCRibbonEdit` controlar cuando cambia el diseño de la dirección.|
|[CMFCRibbonEdit::OnShow](#onshow)|Lo llama el marco para mostrar u ocultar el `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::Redraw](#redraw)|Actualiza la presentación de la `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Establece los datos de accesibilidad para el `CMFCRibbonEdit` objeto.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Establece el texto en el cuadro de texto.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Establece la alineación del texto del cuadro de texto.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Establece el ancho del cuadro de texto para el `CMFCRibbonEdit` control.|

## <a name="remarks"></a>Comentarios

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un `CMFCRibbonEdit` objeto, mostrar botones de número situado junto al control de edición y establecer el texto del control de edición. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonEdit.h

##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched

Indica si el alto de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control puede aumentar verticalmente para el alto de una fila de la cinta de opciones.

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="cmfcribbonedit"></a>  CMFCRibbonEdit::CMFCRibbonEdit

Construye un [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

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
[in] Comando de identificador para el `CMFCRibbonEdit` control.

*nWidth*<br/>
[in] El ancho, en píxeles, del cuadro de texto para el `CMFCRibbonEdit` control.

*lpszLabel*<br/>
[in] La etiqueta para el `CMFCRibbonEdit` control.

*nImage*<br/>
[in] Índice de la imagen pequeña que se utilizará para el `CMFCRibbonEdit` control. La colección de imágenes pequeñas se mantiene por la categoría de cinta de opciones de elemento primario.

### <a name="remarks"></a>Comentarios

El `CMFCRibbonEdit` control no utiliza una imagen grande.

##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom

Copia el estado del elemento especificado [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) el objeto actual [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] El origen `CMFCRibbonEdit` objeto.

### <a name="remarks"></a>Comentarios

El *src* parámetro debe ser de tipo `CMFCRibbonEdit`.

##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit

Crea un nuevo cuadro de texto para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Un puntero a la ventana primaria de la `CMFCRibbonEdit` objeto.

*dwEditStyle*<br/>
[in] Especifica el estilo del cuadro de texto. Puede combinar los estilos de ventana que aparece en la sección de comentarios con el [estilos de control de edición](/windows/desktop/Controls/edit-control-styles) que se describen en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero para el nuevo cuadro de texto si el método se realizó correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para crear un cuadro de texto personalizado.

Puede aplicar los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) al cuadro de texto:

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl

Destruye el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Comentarios

##  <a name="dropdownlist"></a>  CMFCRibbonEdit::DropDownList

Despliega un cuadro de lista.

```
virtual void DropDownList();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método no hace nada. Invalide este método para un cuadro de lista desplegable.

##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons

Habilita y configura el intervalo del botón de número para el cuadro de texto.

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
[in] El valor mínimo del botón de número.

*nMax*<br/>
[in] El valor máximo del botón de número.

### <a name="remarks"></a>Comentarios

Botones de número muestran arriba y flecha abajo y permiten a los usuarios desplazarse por un conjunto fijo de valores.

##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize

Recupera el tamaño compacto de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` objeto.

### <a name="return-value"></a>Valor devuelto

El tamaño compacto de la `CMFCRibbonEdit` objeto.

### <a name="remarks"></a>Comentarios

##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText

Recupera el texto en el cuadro de texto.

```
CString GetEditText() const;
```

### <a name="return-value"></a>Valor devuelto

El texto en el cuadro de texto.

### <a name="remarks"></a>Comentarios

##  <a name="getintermediatesize"></a>  CMFCRibbonEdit::GetIntermediateSize

Recupera el tamaño intermedio de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` objeto.

### <a name="return-value"></a>Valor devuelto

El tamaño intermedio de la `CMFCRibbonEdit` objeto.

### <a name="remarks"></a>Comentarios

##  <a name="gettextalign"></a>  CMFCRibbonEdit::GetTextAlign

Recupera la alineación del texto en el cuadro de texto.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Valor devuelto

Valor enumerado de alineación del texto. Consulte la sección Comentarios para los valores posibles.

### <a name="remarks"></a>Comentarios

El valor devuelto es uno de los siguientes estilos de control de edición:

- **ES_LEFT** para alineación a la izquierda

- **ES_CENTER** para centrar

- **ES_RIGHT** para alineación a la derecha

Para obtener más información acerca de estos estilos, consulte [Editar estilos de Control](/windows/desktop/Controls/edit-control-styles).

##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth

Recupera el ancho, en píxeles, de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parámetros

*bInFloatyMode*<br/>
[in] TRUE si el `CMFCRibbonEdit` control está en modo flotante; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

El ancho, en píxeles, de la `CMFCRibbonEdit` control.

### <a name="remarks"></a>Comentarios

##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode

Indica si la presentación de tamaño para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control puede ser compacto.

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve TRUE. Invalide este método para indicar si el tamaño de presentación puede ser compact.

##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus

Indica si el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control tiene el foco.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el `CMFCRibbonEdit` control tiene el foco; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode

Indica si la presentación de tamaño para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control puede ser grande.

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

Indica si el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control aparece resaltado.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el `CMFCRibbonEdit` control está resaltado; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect

Lo llama el marco cuando las dimensiones del rectángulo de presentación para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar el cambio.

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.

### <a name="remarks"></a>Comentarios

##  <a name="ondraw"></a>  CMFCRibbonEdit::OnDraw

Lo llama el marco de trabajo para dibujar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.

### <a name="remarks"></a>Comentarios

##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage

Lo llama el marco de trabajo para dibujar la etiqueta de imagen para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.

### <a name="remarks"></a>Comentarios

##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList

Lo llama el marco de trabajo para dibujar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control en un cuadro de lista de comandos.

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
[in] Puntero a un contexto de dispositivo para el `CMFCRibbonEdit` control.

*strText*<br/>
[in] El texto para mostrar [ ] (../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit (clase)").

*nTextOffset*<br/>
[in] Distancia, en píxeles, del lado izquierdo del cuadro de lista para mostrar el texto.

*rect*<br/>
[in] El rectángulo de presentación para el `CMFCRibbonEdit` control.

*bIsSelected*<br/>
[in] No se utiliza este parámetro.

*bHighlighted*<br/>
[in] No se utiliza este parámetro.

### <a name="remarks"></a>Comentarios

El cuadro de lista de comandos muestra los controles de cinta de opciones para habilitar a los usuarios personalizar la barra de herramientas de acceso rápido.

##  <a name="onenable"></a>  CMFCRibbonEdit::OnEnable

Lo llama el marco para habilitar o deshabilitar la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
[in] TRUE para habilitar el control; FALSE para deshabilitar el control.

### <a name="remarks"></a>Comentarios

##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight

Lo llama el marco cuando el puntero entra o sale de los límites del [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parámetros

*bHighlight*<br/>
[in] TRUE si el puntero está en los límites de la `CMFCRibbonEdit` control; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey

Lo llama el marco cuando el usuario presiona un keytip y [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control tiene el foco.

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parámetros

*bIsMenuKey*<br/>
[in] TRUE si keytip muestra un menú emergente; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si se controló el evento; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown

Lo llama el marco de trabajo para actualizar la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar cuando el usuario presiona el botón primario del mouse en el control.

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
[in] No se utiliza este parámetro.

### <a name="remarks"></a>Comentarios

##  <a name="onlbuttonup"></a>  CMFCRibbonEdit::OnLButtonUp

Lo llama el marco cuando el usuario suelta el botón primario del mouse.

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
[in] No se utiliza este parámetro.

### <a name="remarks"></a>Comentarios

##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged

Lo llama el marco de trabajo para actualizar la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar cuando cambia el diseño de la dirección.

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parámetros

*bIsRTL*<br/>
[in] TRUE si el diseño es de derecha a izquierda; FALSE si el diseño de izquierda a derecha.

### <a name="remarks"></a>Comentarios

##  <a name="onshow"></a>  CMFCRibbonEdit::OnShow

Lo llama el marco para mostrar u ocultar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
[in] TRUE para mostrar el control; FALSE para ocultar el control.

### <a name="remarks"></a>Comentarios

##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw

Actualiza la presentación de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
virtual void Redraw();
```

### <a name="remarks"></a>Comentarios

Este método vuelve a dibujar el rectángulo de presentación para el `CMFCRibbonEdit` objeto llamando indirectamente [CWnd::RedrawWindow](/windows/desktop/api/winuser/nf-winuser-redrawwindow) con las marcas RDW_INVALIDATE RDW_ERASE y RDW_UPDATENOW establecido.

##  <a name="setaccdata"></a>  CMFCRibbonEdit::SetACCData

Establece los datos de accesibilidad para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
Puntero a la ventana primaria para el `CMFCRibbonEdit` objeto.

*data*<br/>
Los datos de accesibilidad para el `CMFCRibbonEdit` objeto.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText

Establece el texto en el cuadro de texto.

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parámetros

*strText*<br/>
[in] El texto del cuadro de texto.

##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign

Establece la alineación del texto del cuadro de texto.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parámetros

*nAlign*<br/>
[in] Valor enumerado de alineación del texto. Consulte la sección Comentarios para los valores posibles.

### <a name="remarks"></a>Comentarios

El parámetro *nAlign* es uno de la siguiente edición estilos de control:

- ES_LEFT para alineación a la izquierda

- ES_CENTER para centrar

- ES_RIGHT para alineación a la derecha

Para obtener más información acerca de estos estilos, consulte [Editar estilos de Control](/windows/desktop/Controls/edit-control-styles).

##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth

Establece el ancho del cuadro de texto para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
[in] El ancho, en píxeles, del cuadro de texto.

*bInFloatyMode*<br/>
TRUE para establecer el ancho del modo flotante; FALSE para establecer el ancho del modo normal.

### <a name="remarks"></a>Comentarios

El `CMFCRibbonEdit` control tiene dos anchos según su modo de presentación: flotante modo y el modo normal.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
