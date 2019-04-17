---
title: CMFCColorPickerCtrl (clase)
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: 1977717ee590acb63655ba21bfa5eb6bfe7c9bd8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772363"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl (clase)

La `CMFCColorPickerCtrl` clase proporciona funcionalidad para un control que se utiliza para seleccionar colores.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Construye un objeto `CMFCColorPickerCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Recupera el color que el usuario seleccione.|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Recupera los valores de matiz, luminancia y la saturación del color que el usuario seleccione.|
|[CMFCColorPickerCtrl::GetHue](#gethue)|Recupera el componente de matiz del color que el usuario seleccione.|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Recupera el componente de luminancia del color que el usuario seleccione.|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Recupera el componente de saturación del color que el usuario seleccione.|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Establece el color actual en el color definido por los componentes de color RGB especificados o el Hexágono celda especificada.|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Establece el color actual en el valor de color RGB especificado.|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Establece el color actual en el valor de color HLS especificado.|
|[CMFCColorPickerCtrl::SetHue](#sethue)|Cambia el componente de matiz del color seleccionado actualmente.|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Cambia el componente de luminancia del color seleccionado actualmente.|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Establece el ancho de la barra de luminancia en el control de selector de color.|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Establece el color inicial seleccionado.|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Establece la paleta de colores actual.|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Cambia el componente de saturación del color seleccionado actualmente.|
|[CMFCColorPickerCtrl::SetType](#settype)|Establece el tipo de control de selector de color para mostrar.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Lo llama el marco de trabajo antes de que se muestra un cursor que apunta al color seleccionado.|

## <a name="remarks"></a>Comentarios

Colores estándar se seleccionan de una paleta de colores hexagonal y colores personalizados están seleccionados de una barra de luminancia donde los colores se especifican utilizando la notación rojo/verde/azul o notación de matiz/satuaration/luminancia.

La siguiente ilustración muestra varios `CMFCColorPickerCtrl` objetos.

![Cuadro de diálogo CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "cuadro de diálogo CMFCColorPickerCtrl")

El `CMFCColorPickerCtrl` admite dos pares de estilos. Los estilos HEX_GREYSCALE y valores HEXADECIMALES son adecuados para la selección de color estándar. Los estilos de SELECTOR y la LUMINANCIA son adecuados para la selección de color personalizado.

Siga estos pasos para incorporar el `CMFCColorPickerCtrl` control en el cuadro de diálogo:

1. Si usas el **ClassWizard**, inserte un nuevo control de botón en la plantilla de cuadro de diálogo (porque el `CMFCColorPickerCtrl` clase se hereda de la `CButton` clase).

1. Insertar una variable de miembro que está asociada con el nuevo control de botón en la clase del cuadro de diálogo. A continuación, cambie el tipo de variable de `CButton` a `CMFCColorPickerCtrl`.

1. Insertar el `WM_INITDIALOG` controlador de mensajes para la clase de cuadro de diálogo. En el controlador, establezca el tipo, la paleta y el color seleccionado inicial de la `CMFCColorPickerCtrl` control.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar un `CMFCColorPickerCtrl` objeto mediante distintos métodos en el `CMFCColorPickerCtrl` clase. El ejemplo muestra cómo establecer el tipo de control de selector de y cómo establecer su color, matiz, luminancia y saturación. El ejemplo forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolorpickerctrl.h

##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl

Construye un objeto `CMFCColorPickerCtrl`.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor

Lo llama el marco de trabajo antes de que se muestra un cursor que apunta al color seleccionado.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero a un contexto de dispositivo.

*rect*<br/>
[in] Especifica un área rectangular alrededor del color seleccionado.

### <a name="remarks"></a>Comentarios

Invalide este método cuando necesite cambiar la forma del cursor que apunta al color seleccionado.

##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor

Recupera el color que el usuario seleccione.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El valor RGB del color seleccionado.

### <a name="remarks"></a>Comentarios

##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS

Recupera los valores de matiz, luminancia y la saturación del color que el usuario seleccione.

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Parámetros

*hue*<br/>
[out] Puntero a una variable de tipo double que recibe información de hue.

*luminance*<br/>
[out] Puntero a una variable de tipo double que recibe información de luminancia.

*saturation*<br/>
[out] Puntero a una variable de tipo double que recibe información de la saturación.

### <a name="remarks"></a>Comentarios

##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue

Recupera el componente de matiz del color que el usuario seleccione.

```
double GetHue() const;
```

### <a name="return-value"></a>Valor devuelto

El componente de matiz del color seleccionado.

### <a name="remarks"></a>Comentarios

##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance

Recupera el componente de luminancia del color que el usuario seleccione.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Valor devuelto

El componente de luminancia del color seleccionado.

### <a name="remarks"></a>Comentarios

##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation

Recupera el valor de saturación del color que el usuario seleccione.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Valor devuelto

El componente de saturación del color seleccionado.

### <a name="remarks"></a>Comentarios

##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon

Establece el color actual en el color definido por los componentes de color RGB especificados o el Hexágono celda especificada.

```
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
[in] El componente de color rojo.

*G*<br/>
[in] El componente de color verde.

*B*<br/>
[in] El componente de color azul.

*x*<br/>
[in] La coordenada x del cursor, que señala a un hexágono de celda.

*y*<br/>
[in] Coordenada y del cursor, que señala a un hexágono de celda.

### <a name="return-value"></a>Valor devuelto

La segunda sobrecarga de este método siempre devuelve FALSE.

### <a name="remarks"></a>Comentarios

La primera sobrecarga de este método establece el color que se corresponde con el control de selección de color al color actual especificado del componentes de color rojo, verde y azul.

La segunda sobrecarga de este método establece el color actual al color del Hexágono celda que se ha señalado por la ubicación del cursor especificado.

##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor

Establece el color actual en el valor de color RGB especificado.

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[in] Un valor de color RGB.

### <a name="remarks"></a>Comentarios

##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS

Establece el color actual en el valor de color HLS especificado.

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Parámetros

*hue*<br/>
[in] Un valor de matiz.

*luminance*<br/>
[in] Un valor de luminancia.

*saturation*<br/>
[in] Un valor de saturación.

*bInvalidate*<br/>
[in] TRUE para forzar la ventana para actualizar inmediatamente el nuevo color; en caso contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue

Cambia el matiz del color seleccionado actualmente.

```
void SetHue(double Hue);
```

### <a name="parameters"></a>Parámetros

*HUE*<br/>
[in] Un valor de matiz.

### <a name="remarks"></a>Comentarios

##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance

Cambia la luminancia del color seleccionado actualmente.

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Parámetros

*Luminancia*<br/>
[in] Un valor de luminancia.

### <a name="remarks"></a>Comentarios

##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth

Establece el ancho de la barra de luminancia en el control de selector de color.

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Parámetros

*w*<br/>
[in] El ancho de la barra de luminancia medido en píxeles.

### <a name="remarks"></a>Comentarios

Use este método para cambiar el tamaño de la barra de luminancia, que se encuentra en la **personalizado** pestaña de control de selector de color. El *w* parámetro especifica el nuevo ancho de la barra de luminancia. Si supera tres cuartas partes del ancho del área de cliente, se omite el valor de ancho.

##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor

Establece el color inicial seleccionado.

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Parámetros

*ref*<br/>
[in] Un valor de color RGB.

### <a name="remarks"></a>Comentarios

Llame a este método cuando se inicializa el control de selector de color.

##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette

Establece la paleta de colores actual.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parámetros

*pPalette*<br/>
[in] Puntero a una paleta de colores.

### <a name="remarks"></a>Comentarios

La paleta de colores define la matriz de colores que se presenta en el control de selector de color.

##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation

Cambia la saturación del color seleccionado actualmente.

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Parámetros

*Saturación*<br/>
[in] Un valor de saturación.

### <a name="remarks"></a>Comentarios

##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType

Establece el tipo de control de selector de color para mostrar.

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Parámetros

*colorType*<br/>
[in] Un tipo de control de selector de color.

Los tipos definidos por el `CMFCColorPickerCtrl::COLORTYPE` enumeración. Los tipos posibles son LUMINANCIA, SELECTOR, HEXADECIMAL y HEX_GREYSCALE. El tipo predeterminado es SELECTOR.

### <a name="remarks"></a>Comentarios

Para especificar un tipo de control de selector de color, llame a este método antes de crea el control de Windows.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md)
