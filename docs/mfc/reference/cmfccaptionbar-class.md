---
title: CMFCCaptionBar (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: 3a1e8890176fe686b54fe4756dfd578869cbcdfb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367793"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar (clase)

Un `CMFCCaptionBar` objeto es una barra de control que puede mostrar tres elementos: un botón, una etiqueta de texto y un mapa de bits. Puede mostrar un solo elemento de cada tipo al mismo tiempo. Puede alinear cada elemento al borde izquierdo o derecho del control o al centro. También puede aplicar un estilo plano o 3D a los bordes superior e inferior de la barra de título.

## <a name="syntax"></a>Sintaxis

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCCaptionBar::Crear](#create)|Crea el control de barra de `CMFCCaptionBar` título y lo adjunta al objeto.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Indica si se puede insertar dinámicamente otro panel entre la barra de título y su marco primario. (Reemplaza [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|Habilita o deshabilita el botón de la barra de subtítulos.|
|[CMFCCaptionBar::GetAlignment](#getalignment)|Devuelve la alineación del elemento especificado.|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Devuelve el tamaño del borde de la barra de título.|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Recupera el rectángulo delimitador del botón de la barra de título.|
|[CMFCCaptionBar::GetMargin](#getmargin)|Devuelve la distancia entre el borde de los elementos de la barra de título y el borde del control de barra de título.|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Especifica si la barra de título está en el modo de barra de mensajes.|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Elimina la imagen de mapa de bits de la barra de título.|
|[CMFCCaptionBar::RemoveButton](#removebutton)|Elimina el botón de la barra de subtítulos.|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Elimina el icono de la barra de subtítulos.|
|[CMFCCaptionBar::RemoveText](#removetext)|Elimina la etiqueta de texto de la barra de título.|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Establece la imagen de mapa de bits para la barra de título.|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Establece el tamaño del borde de la barra de título.|
|[CMFCCaptionBar::SetButton](#setbutton)|Establece el botón de la barra de título.|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Especifica si el botón permanece pulsado.|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Establece la información sobre herramientas del botón.|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Establece el estilo de borde de la barra de título.|
|[CMFCCaptionBar::SetIcon](#seticon)|Establece el icono de una barra de título.|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Establece la información sobre herramientas de la imagen de la barra de título.|
|[CMFCCaptionBar::SetMargin](#setmargin)|Establece la distancia entre el borde del elemento de barra de título y el borde del control de barra de título.|
|[CMFCCaptionBar::SetText](#settext)|Establece la etiqueta de texto de la barra de título.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Llamado por el marco de trabajo para rellenar el fondo de la barra de título.|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Llamado por el marco de trabajo para dibujar el borde de la barra de título.|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Llamado por el marco de trabajo para dibujar el botón de la barra de título.|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Llamado por el marco de trabajo para dibujar la imagen de la barra de título.|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Llamado por el marco de trabajo para dibujar el texto de la barra de título.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|El color de fondo de la barra de título.|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|El color del borde de la barra de título.|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|El color del texto de la barra de título.|

## <a name="remarks"></a>Observaciones

Para crear una barra de subtítulos, siga estos pasos:

1. Construir `CMFCCaptionBar` el objeto. Normalmente, agregaría la barra de título a una clase de ventana de marco.

1. Llame a la [CMFCCaptionBar::Create](#create) método para crear el `CMFCCaptionBar` control de barra de título y adjuntarlo al objeto.

1. Llame a [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon)y [CMFCCaptionBar::SetBitmap](#setbitmap) para establecer los elementos de la barra de título.

Al establecer el elemento button, debe asignar un identificador de comando al botón. Cuando el usuario hace clic en el botón, la barra de título enruta los mensajes WM_COMMAND que tienen este identificador a la ventana de marco principal.

La barra de título también puede funcionar en modo de barra de mensajes, que emula la barra de mensajes que aparece en las aplicaciones de Microsoft Office 2007. En el modo de barra de mensajes, la barra de subtítulos muestra un mapa de bits, un mensaje y un botón (que normalmente abre un cuadro de diálogo.) Puede asignar una información sobre herramientas al mapa de bits.

Para habilitar el modo de barra de mensajes, llame a [CMFCCaptionBar::Create](#create) y establezca el cuarto parámetro (bIsMessageBarMode) en TRUE.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCCaptionBar` . En el ejemplo se muestra cómo crear el control de barra de título, establecer un borde 3D de la barra de título, establecer la distancia, en píxeles, entre el borde de los elementos de la barra de título y el borde del control de la barra de título, establecer el botón para la barra de título, establecer la información sobre herramientas para el botón, establecer la etiqueta de texto para la barra de título, establecer la imagen de mapa de bits para la barra de título , y establezca la información sobre herramientas de la imagen en la barra de título. Este fragmento de código forma parte del ejemplo de demostración de [MS Office 2007.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcaptionbar.h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a>CMFCCaptionBar::Crear

Crea el control de barra de `CMFCCaptionBar` título y lo adjunta al objeto.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
La combinación OR lógica de los estilos de barra de título.

*pParentWnd*<br/>
La ventana primaria del control de barra de título.

*Uid*<br/>
El identificador del control de barra de título.

*nAltura*<br/>
Altura, en píxeles, del control de barra de título. Si es -1, la altura se calcula según la altura del icono, el texto y el botón que muestra el control de barra de título.

*bIsMessageBarMode*<br/>
TRUESi la barra de título está en el modo de barra de mensajes; FALSE en caso contrario.

### <a name="return-value"></a>Valor devuelto

TRUESi el control de barra de título se crea correctamente; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Construir un `CMFCCaptionBar` objeto en dos pasos. En primer lugar, llame al `Create` constructor y, a continuación, llame al `CMFCCaptionBar` método, que crea el control de Windows y lo adjunta al objeto.

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCCaptionBar::DoesAllowDynInsertBefore

Indica si se puede insertar dinámicamente otro panel entre la barra de título y su marco primario.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE a menos que se invalide.

### <a name="remarks"></a>Observaciones

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a>CMFCCaptionBar::EnableButton

Habilita o deshabilita el botón de la barra de subtítulos.

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE Para habilitar el botón, FALSE para deshabilitar el botón.

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a>CMFCCaptionBar::GetAlignment

Devuelve la alineación del elemento especificado.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Parámetros

*Elem*<br/>
[en] Un elemento de barra de título para el que se va a recuperar la alineación.

### <a name="return-value"></a>Valor devuelto

Alineación de un elemento, como un botón, un mapa de bits, texto o un icono.

### <a name="remarks"></a>Observaciones

La alineación del elemento puede ser uno de los siguientes valores:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a>CMFCCaptionBar::GetBorderSize

Devuelve el tamaño del borde de la barra de título.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño, en píxeles, del borde.

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a>CMFCCaptionBar::GetButtonRect

Recupera el rectángulo delimitador del botón de la barra de título.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `CRect` que contiene las coordenadas del rectángulo delimitador del botón de la barra de título.

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a>CMFCCaptionBar::GetMargin

Devuelve la distancia entre el borde de los elementos de la barra de título y el borde del control de barra de título.

```
int GetMargin() const;
```

### <a name="return-value"></a>Valor devuelto

La distancia, en píxeles, entre el borde de los elementos de la barra de título y el borde del control de barra de título.

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a>CMFCCaptionBar::IsMessageBarMode

Especifica si la barra de título está en el modo de barra de mensajes.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la barra de título está en el modo de barra de mensajes; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

En el modo de barra de mensajes, la barra de título muestra una imagen con información sobre herramientas, un texto de mensaje y un botón.

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a>CMFCCaptionBar::m_clrBarBackground

El color de fondo de la barra de título.

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a>CMFCCaptionBar::m_clrBarBorder

El color del borde de la barra de título.

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a>CMFCCaptionBar::m_clrBarText

El color del texto de la barra de título.

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a>CMFCCaptionBar::OnDrawBackground

Llamado por el marco de trabajo para rellenar el fondo de la barra de título.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Un puntero al contexto del dispositivo de la barra de título.

*Rect*<br/>
[en] El rectángulo delimitador que se va a rellenar.

### <a name="remarks"></a>Observaciones

Se `OnDrawBackground` llama al método cuando el fondo de la barra de título está a punto de rellenarse. La implementación predeterminada rellena el fondo mediante el [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) color.

Invalide este `CMFCCaptionBar` método en una clase derivada para personalizar la apariencia de la barra de título.

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a>CMFCCaptionBar::OnDrawBorder

Llamado por el marco de trabajo para dibujar el borde de la barra de título.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Contexto de dispositivo que se utiliza para mostrar los bordes.

*Rect*<br/>
[en] El rectángulo delimitador.

### <a name="remarks"></a>Observaciones

De forma predeterminada, los bordes tienen el estilo plano.

Invalide este `CMFCCaptionBar` método en una clase derivada para personalizar la apariencia de los bordes de la barra de título.

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a>CMFCCaptionBar::OnDrawButton

Llamado por el marco de trabajo para dibujar el botón de la barra de título.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo que se utiliza para mostrar el botón.

*Rect*<br/>
[en] El rectángulo delimitador del botón.

*strButton*<br/>
[en] Etiqueta de texto del botón.

*bHabilitado*<br/>
[en] TRUESi el botón está habilitado; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Invalide este `CMFCCaptionBar` método en una clase derivada para personalizar la apariencia del botón de la barra de título.

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a>CMFCCaptionBar::OnDrawImage

Llamado por el marco de trabajo para dibujar la imagen de la barra de título.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo que se utiliza para mostrar la imagen.

*Rect*<br/>
[en] Especifica el rectángulo delimitador de la imagen.

### <a name="remarks"></a>Observaciones

Invalide este `CMFCCaptionBar` método en una clase derivada para personalizar la apariencia de la imagen.

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a>CMFCCaptionBar::OnDrawText

Llamado por el marco de trabajo para dibujar el texto de la barra de título.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo que se utiliza para mostrar el botón.

*Rect*<br/>
[en] El rectángulo delimitador del texto.

*strText*<br/>
[en] La cadena de texto que se va a mostrar.

### <a name="remarks"></a>Observaciones

La implementación predeterminada muestra `CDC::DrawText` el texto mediante using and [CMFCCaptionBar::m_clrBarText](#m_clrbartext) color.

Invalide este `CMFCCaptionBar` método en una clase derivada para personalizar la apariencia del texto de la barra de título.

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a>CMFCCaptionBar::RemoveBitmap

Elimina la imagen de mapa de bits de la barra de título.

```
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a>CMFCCaptionBar::RemoveButton

Elimina el botón de la barra de subtítulos.

```
void RemoveButton();
```

### <a name="remarks"></a>Observaciones

El diseño de los elementos de la barra de título se ajusta automáticamente.

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a>CMFCCaptionBar::RemoveIcon

Elimina el icono de la barra de subtítulos.

```
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a>CMFCCaptionBar::RemoveText

Elimina la etiqueta de texto de la barra de título.

```
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a>CMFCCaptionBar::SetBitmap

Establece la imagen de mapa de bits para la barra de título.

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
[en] El identificador del mapa de bits que se ha establecido.

*clrTransparent*<br/>
[en] Un valor RGB que especifica el color transparente del mapa de bits.

*bStretch*<br/>
[en] Si es TRUE, el mapa de bits se estira si no se ajusta al rectángulo delimitador de la imagen. De lo contrario, el mapa de bits no se estira.

*bmpAlignment*<br/>
[en] La alineación del mapa de bits.

### <a name="remarks"></a>Observaciones

Utilice este método para establecer un mapa de bits en una barra de título.

El mapa de bits anterior se destruye automáticamente. Si la barra de subtítulos muestra un icono porque llamó al método [CMFCCaptionBar::SetIcon,](#seticon) el mapa de bits no se mostrará a menos que quite el icono llamando a [CMFCCaptionBar::RemoveIcon](#removeicon).

El mapa de bits se alinea según lo especificado por el *bmpAlignment* parámetro.  Este parámetro puede ser uno de los siguientes valores `BarElementAlignment`:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a>CMFCCaptionBar::SetBorderSize

Establece el tamaño del borde de la barra de título.

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nTamaño*<br/>
[en] El nuevo tamaño, en píxeles, del borde de la barra de título.

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a>CMFCCaptionBar::SetButton

Establece el botón de la barra de título.

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
La etiqueta de comando del botón.

*uiCmdUI*<br/>
El ID de comando del botón.

*btnAlignmnet*<br/>
Alineación del botón.

*bHasDropDownArrow*<br/>
TRUESi el botón muestra una flecha desplegable, FALSE en caso contrario.

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a>CMFCCaptionBar::SetButtonPressed

Especifica si el botón permanece pulsado.

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Parámetros

*bPresed*<br/>
TRUESi el botón mantiene su estado presionado, FALSE en caso contrario.

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a>CMFCCaptionBar::SetButtonToolTip

Establece la información sobre herramientas del botón.

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszToolTip*<br/>
[en] El título de información sobre herramientas.

*lpszDescription*<br/>
[en] La descripción de la información sobre herramientas.

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a>CMFCCaptionBar::SetFlatBorder

Establece el estilo de borde de la barra de título.

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parámetros

*bFlat*<br/>
[en] TRUESi el borde de una barra de título es plano. FALSE si el borde es 3D.

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a>CMFCCaptionBar::SetIcon

Establece el icono de una barra de título.

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
[en] El identificador del icono que se ha establecido.

*iconoAlineación*<br/>
[en] La alineación del icono.

### <a name="remarks"></a>Observaciones

Las barras de subtítulos pueden mostrar iconos o mapas de bits. Consulte [CMFCCaptionBar::SetBitmap](#setbitmap) para averiguar cómo mostrar un mapa de bits. Si establece un icono y un mapa de bits, el icono siempre se muestra. Llame a [CMFCCaptionBar::RemoveIcon](#removeicon) para quitar un icono de la barra de título.

El icono se alinea según el parámetro *iconAlignment.* Puede ser uno de `BarElementAlignment` los siguientes valores:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a>CMFCCaptionBar::SetImageToolTip

Establece la información sobre herramientas de la imagen en la barra de título.

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszToolTip*<br/>
[en] El texto de la información sobre herramientas.

*lpszDescription*<br/>
[en] La descripción de la información sobre herramientas.

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a>CMFCCaptionBar::SetMargin

Establece la distancia entre el borde del elemento de barra de título y el borde del control de barra de título.

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Parámetros

*nMargin*<br/>
[en] La distancia, en píxeles, entre el borde de los elementos de la barra de título y el borde del control de barra de título.

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a>CMFCCaptionBar::SetText

Establece la etiqueta de texto de la barra de título.

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parámetros

*strText*<br/>
[en] Cadena de texto que se va a establecer.

*textAlignment*<br/>
[en] La alineación del texto.

### <a name="remarks"></a>Observaciones

La etiqueta de texto se alinea según lo especificado por el parámetro *textAlignment.* Puede ser uno de `BarElementAlignment` los siguientes valores:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
