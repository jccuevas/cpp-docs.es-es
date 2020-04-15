---
title: CMFCRibbonEdit Clase
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
ms.openlocfilehash: ab621a05f9b658eee9babb14e257680fa95e0f96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375177"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit Clase

Implementa un control de edición que se encuentra en una barra de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```cpp
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonEdit::CanBestretched](#canbestretched)|Indica si el alto `CMFCRibbonEdit` del control puede aumentar verticalmente hasta el alto de una fila de cinta de opciones.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construye un objeto `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copia el estado del `CMFCRibbonEdit` objeto especificado `CMFCRibbonEdit` en el objeto actual.|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Crea un nuevo cuadro `CMFCRibbonEdit` de texto para el objeto.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Destruye el objeto `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Despliega un cuadro de lista.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Habilita y establece el rango del botón de giro para el cuadro de texto.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Recupera el tamaño compacto `CFMCRibbonEdit` del objeto.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Recupera el texto del cuadro de texto.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Recupera el tamaño intermedio `CMFCRibbonEdit` del objeto.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Recupera la alineación del texto en el cuadro de texto.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Recupera el ancho, en píxeles, del `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indica si el tamaño `CMFCRibbonEdit` de visualización del control puede ser compacto.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indica si `CMFCRIbbonEdit` el control tiene el foco.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indica si el tamaño `CMFCRibbonEdit` de visualización del control puede ser grande.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indica si el cuadro de texto tiene un botón de giro.|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indica si `CMFCRibbonEdit` el control está resaltado.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Llamado por el marco de trabajo cuando `CMFCRibbonEdit` cambian las dimensiones del rectángulo de visualización para el control.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Llamado por el marco `CMFCRibbonEdit` de trabajo para dibujar el control.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Llamado por el marco de trabajo `CMFCRibbonEdit` para dibujar la etiqueta y la imagen para el control.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Llamado por el marco `CMFCRibbonEdit` de trabajo para dibujar el control en un cuadro de lista de comandos.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Llamado por el marco de `CMFCRibbonEdit` trabajo para habilitar o deshabilitar el control.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Llamado por el marco de trabajo cuando el `CMFCRibbonEdit` puntero entra o sale de los límites del control.|
|[CMFCRibbonEdit::OnKey](#onkey)|Llamado por el marco de trabajo cuando `CMFCRibbonEdit` el usuario presiona una información clave y el control tiene el foco.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Llamado por el marco `CMFCRibbonEdit` de trabajo para actualizar el control cuando el usuario presiona el botón izquierdo del mouse en el control.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Llamado por el marco de trabajo cuando el usuario suelta el botón izquierdo del mouse.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Llamado por el marco `CMFCRibbonEdit` de trabajo para actualizar el control cuando el diseño cambia de dirección.|
|[CMFCRibbonEdit::OnShow](#onshow)|Llamado por el marco de `CMFCRibbonEdit` trabajo para mostrar u ocultar el control.|
|[CMFCRibbonEdit::Redibujar](#redraw)|Actualiza la visualización del `CMFCRibbonEdit` control.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Establece los datos de `CMFCRibbonEdit` accesibilidad para el objeto.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Establece el texto en el cuadro de texto.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Establece la alineación del texto del cuadro de texto.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Establece el ancho del cuadro `CMFCRibbonEdit` de texto para el control.|

## <a name="remarks"></a>Observaciones

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCRibbonEdit` muestra cómo construir un objeto, mostrar botones de giro junto al control de edición y establecer el texto del control de edición. Este fragmento de código forma parte del ejemplo de demostración de [MS Office 2007.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonEdit.h

## <a name="cmfcribboneditcanbestretched"></a><a name="canbestretched"></a>CMFCRibbonEdit::CanBestretched

Indica si el alto del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) puede aumentar verticalmente hasta el alto de una fila de la cinta de opciones.

```cpp
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditcmfcribbonedit"></a><a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit

Construye un [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```cpp
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] Identificador de `CMFCRibbonEdit` comando para el control.

*nAncho*<br/>
[en] El ancho, en píxeles, del `CMFCRibbonEdit` cuadro de texto para el control.

*lpszLabel*<br/>
[en] La etiqueta `CMFCRibbonEdit` del control.

*nImage*<br/>
[en] Index de la imagen pequeña `CMFCRibbonEdit` que se va a utilizar para el control. La colección de imágenes pequeñas se mantiene mediante la categoría de cinta de opciones principal.

### <a name="remarks"></a>Observaciones

El `CMFCRibbonEdit` control no utiliza una imagen grande.

## <a name="cmfcribboneditcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom

Copia el estado del objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) especificado en el objeto [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) actual.

```cpp
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] El `CMFCRibbonEdit` objeto de origen.

### <a name="remarks"></a>Observaciones

El parámetro *src* debe `CMFCRibbonEdit`ser de tipo .

## <a name="cmfcribboneditcreateedit"></a><a name="createedit"></a>CMFCRibbonEdit::CreateEdit

Crea un nuevo cuadro de texto para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```cpp
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la `CMFCRibbonEdit` ventana primaria del objeto.

*dwEditStyle*<br/>
[en] Especifica el estilo del cuadro de texto. Puede combinar los estilos de ventana enumerados en la sección Comentarios con los estilos de control de [edición](/windows/win32/Controls/edit-control-styles) que se describen en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Un puntero al nuevo cuadro de texto si el método se realizó correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para crear un cuadro de texto personalizado.

Puede aplicar los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a un cuadro de texto:

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

## <a name="cmfcribboneditdestroyctrl"></a><a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl

Destruye el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```cpp
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditdropdownlist"></a><a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList

Despliega un cuadro de lista.

```cpp
virtual void DropDownList();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método no hace nada. Invalide este método para colocar un cuadro de lista.

## <a name="cmfcribboneditenablespinbuttons"></a><a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons

Habilita y establece el rango del botón de giro para el cuadro de texto.

```cpp
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
[en] El valor mínimo del botón de giro.

*nMax*<br/>
[en] El valor máximo del botón de giro.

### <a name="remarks"></a>Observaciones

Los botones de giro muestran una flecha hacia arriba y hacia abajo y permiten a los usuarios moverse a través de un conjunto fijo de valores.

## <a name="cmfcribboneditgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize

Recupera el tamaño compacto de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```cpp
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto `CMFCRibbonEdit` de dispositivo para el objeto.

### <a name="return-value"></a>Valor devuelto

El tamaño compacto `CMFCRibbonEdit` del objeto.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditgetedittext"></a><a name="getedittext"></a>CMFCRibbonEdit::GetEditText

Recupera el texto del cuadro de texto.

```cpp
CString GetEditText() const;
```

### <a name="return-value"></a>Valor devuelto

El texto del cuadro de texto.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize

Recupera el tamaño intermedio de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto `CMFCRibbonEdit` de dispositivo para el objeto.

### <a name="return-value"></a>Valor devuelto

El tamaño intermedio `CMFCRibbonEdit` del objeto.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditgettextalign"></a><a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign

Recupera la alineación del texto en el cuadro de texto.

```cpp
int GetTextAlign() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor enumerado de alineación de texto. Consulte la sección Comentarios para ver los valores posibles.

### <a name="remarks"></a>Observaciones

El valor devuelto es uno de los siguientes estilos de control de edición:

- **ES_LEFT** para la alineación izquierda

- **ES_CENTER** para la alineación del centro

- **ES_RIGHT** para la alineación correcta

Para obtener más información acerca de estos estilos, vea [Editar estilos](/windows/win32/Controls/edit-control-styles)de control .

## <a name="cmfcribboneditgetwidth"></a><a name="getwidth"></a>CMFCRibbonEdit::GetWidth

Recupera el ancho, en píxeles, de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parámetros

*bInFloatyMode*<br/>
[en] TRUESi `CMFCRibbonEdit` el control está en modo flotante; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

El ancho, en píxeles, del `CMFCRibbonEdit` control.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonedithascompactmode"></a><a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

Indica si el tamaño de visualización del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) puede ser compacto.

```cpp
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método siempre devuelve TRUE. Invalide este método para indicar si el tamaño de visualización puede ser compacto.

## <a name="cmfcribbonedithasfocus"></a><a name="hasfocus"></a>CMFCRibbonEdit::HasFocus

Indica si el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control tiene el foco.

```cpp
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi `CMFCRibbonEdit` el control tiene el foco; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonedithaslargemode"></a><a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

Indica si el tamaño de visualización del control [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) puede ser grande.

```cpp
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve FALSE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método siempre devuelve FALSE. Invalide este método para indicar si el tamaño de visualización puede ser grande.

## <a name="cmfcribbonedithasspinbuttons"></a><a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons

Indica si el cuadro de texto tiene un botón de giro.

```cpp
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el cuadro de texto tiene un botón de giro; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditishighlighted"></a><a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted

Indica si el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control está resaltado.

```cpp
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi `CMFCRibbonEdit` se resalta el control; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditonafterchangerect"></a><a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

Llamado por el marco de trabajo cuando cambian las dimensiones del rectángulo de visualización para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto `CMFCRibbonEdit` de dispositivo para el control.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditondraw"></a><a name="ondraw"></a>CMFCRibbonEdit::OnDraw

Llamado por el marco de trabajo para dibujar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto `CMFCRibbonEdit` de dispositivo para el control.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditondrawlabelandimage"></a><a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

Llamado por el marco de trabajo para dibujar la etiqueta y la imagen para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto `CMFCRibbonEdit` de dispositivo para el control.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList

Llamado por el marco de trabajo para dibujar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control en un cuadro de lista de comandos.

```cpp
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
[en] Puntero a un contexto `CMFCRibbonEdit` de dispositivo para el control.

*strText*<br/>
[en] El texto [ ](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit clase")de visualización .

*nTextOffset*<br/>
[en] Distancia, en píxeles, desde el lado izquierdo del cuadro de lista hasta el texto de visualización.

*Rect*<br/>
[en] El rectángulo de `CMFCRibbonEdit` visualización para el control.

*bIsSelected*<br/>
[en] Este parámetro no se utiliza.

*bResaltado*<br/>
[en] Este parámetro no se utiliza.

### <a name="remarks"></a>Observaciones

El cuadro de lista comandos muestra los controles de la cinta de opciones para permitir a los usuarios personalizar la barra de herramientas de acceso rápido.

## <a name="cmfcribboneditonenable"></a><a name="onenable"></a>CMFCRibbonEdit::OnEnable

Llamado por el marco de trabajo para habilitar o deshabilitar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para habilitar el control; FALSE para deshabilitar el control.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditonhighlight"></a><a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight

Llamado por el marco de trabajo cuando el puntero entra o sale de los límites de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parámetros

*bResaltar*<br/>
[en] TRUESi el puntero está en `CMFCRibbonEdit` los límites del control; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditonkey"></a><a name="onkey"></a>CMFCRibbonEdit::OnKey

Llamado por el marco de trabajo cuando el usuario presiona una información clave y el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control tiene el foco.

```cpp
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parámetros

*bIsMenuKey*<br/>
[en] TRUESi la información sobre teclas muestra un menú emergente; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUESi se controló el evento; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditonlbuttondown"></a><a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown

Llamado por el marco de trabajo para actualizar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control cuando el usuario presiona el botón izquierdo del mouse en el control.

```cpp
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
[en] Este parámetro no se utiliza.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditonlbuttonup"></a><a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

Llamado por el marco de trabajo cuando el usuario suelta el botón izquierdo del mouse.

```cpp
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
[en] Este parámetro no se utiliza.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditonrtlchanged"></a><a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged

Llamado por el marco de trabajo para actualizar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control cuando el diseño cambia de dirección.

```cpp
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parámetros

*bIsRTL*<br/>
[en] TRUESi el diseño es de derecha a izquierda; FALSE si el diseño es de izquierda a derecha.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditonshow"></a><a name="onshow"></a>CMFCRibbonEdit::OnShow

Llamado por el marco de trabajo para mostrar u ocultar el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[en] TRUE para mostrar el control; FALSE para ocultar el control.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditredraw"></a><a name="redraw"></a>CMFCRibbonEdit::Redibujar

Actualiza la presentación de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Observaciones

Este método vuelve a dibujar `CMFCRibbonEdit` el rectángulo de presentación para el objeto mediante una llamada indirecta a [CWnd::RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) con los RDW_INVALIDATE, RDW_ERASE y RDW_UPDATENOW marcas establecidas.

## <a name="cmfcribboneditsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonEdit::SetACCData

Establece los datos de accesibilidad para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.

```cpp
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
Puntero a la ventana `CMFCRibbonEdit` primaria del objeto.

*datos*<br/>
Los datos de `CMFCRibbonEdit` accesibilidad para el objeto.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboneditsetedittext"></a><a name="setedittext"></a>CMFCRibbonEdit::SetEditText

Establece el texto en el cuadro de texto.

```cpp
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parámetros

*strText*<br/>
[en] El texto del cuadro de texto.

## <a name="cmfcribboneditsettextalign"></a><a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign

Establece la alineación del texto del cuadro de texto.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parámetros

*nAlinear*<br/>
[en] Un valor enumerado de alineación de texto. Consulte la sección Comentarios para ver los valores posibles.

### <a name="remarks"></a>Observaciones

El parámetro *nAlign* es uno de los siguientes estilos de control de edición:

- ES_LEFT para la alineación izquierda

- ES_CENTER para la alineación del centro

- ES_RIGHT para la alineación correcta

Para obtener más información acerca de estos estilos, vea [Editar estilos](/windows/win32/Controls/edit-control-styles)de control .

## <a name="cmfcribboneditsetwidth"></a><a name="setwidth"></a>CMFCRibbonEdit::SetWidth

Establece el ancho del cuadro de texto para el [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) control.

```cpp
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
[en] El ancho, en píxeles, del cuadro de texto.

*bInFloatyMode*<br/>
TRUE para establecer el ancho para el modo flotante; FALSE para establecer el ancho para el modo normal.

### <a name="remarks"></a>Observaciones

El `CMFCRibbonEdit` control tiene dos anchos dependiendo de su modo de visualización: modo flotante y modo regular.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
