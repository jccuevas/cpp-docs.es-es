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
ms.openlocfilehash: fe35ee5d6fc6484788a2636151c386689f4bdd96
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752536"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl (clase)

La `CMFCColorPickerCtrl` clase proporciona funcionalidad para un control que se utiliza para seleccionar colores.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Construye un objeto `CMFCColorPickerCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Recupera el color que selecciona el usuario.|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Recupera los valores de matiz, luminancia y saturación del color que el usuario selecciona.|
|[CMFCColorPickerCtrl::GetHue](#gethue)|Recupera el componente de matiz del color que selecciona el usuario.|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Recupera el componente de luminancia del color que selecciona el usuario.|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Recupera el componente de saturación del color que el usuario selecciona.|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Establece el color actual en el color definido por los componentes de color RGB especificados o el hexágono de celda especificado.|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Establece el color actual en el valor de color RGB especificado.|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Establece el color actual en el valor de color HLS especificado.|
|[CMFCColorPickerCtrl::SetHue](#sethue)|Cambia el componente de matiz del color seleccionado actualmente.|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Cambia el componente de luminancia del color seleccionado actualmente.|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Establece el ancho de la barra de luminancia en el control de selector de color.|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Establece el color seleccionado inicialmente.|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Establece la paleta de colores actual.|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Cambia el componente de saturación del color seleccionado actualmente.|
|[CMFCColorPickerCtrl::SetType](#settype)|Establece el tipo de control selector de color que se va a mostrar.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Llamado por el marco de trabajo antes de un cursor que apunta al color seleccionado se muestra.|

## <a name="remarks"></a>Observaciones

Los colores estándar se seleccionan de una paleta de colores hexagonal y los colores personalizados se seleccionan en una barra de luminancia donde los colores se especifican mediante notación rojo/verde/azul o notación de tono/satuaration/luminancia.

En la ilustración `CMFCColorPickerCtrl` siguiente se muestran varios objetos.

![Cuadro de diálogo CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "Cuadro de diálogo CMFCColorPickerCtrl")

Admite `CMFCColorPickerCtrl` dos pares de estilos. Los estilos HEX y HEX_GREYSCALE son adecuados para la selección de color estándar. Los estilos PICKER y LUMINANCE son adecuados para la selección de color personalizada.

Realice los pasos `CMFCColorPickerCtrl` siguientes para incorporar el control en el cuadro de diálogo:

1. Si utiliza **ClassWizard**, inserte un nuevo control de botón en la plantilla de cuadro de diálogo (porque la `CMFCColorPickerCtrl` clase se hereda de la `CButton` clase).

1. Inserte una variable miembro asociada con el nuevo control de botón en la clase de cuadro de diálogo. A continuación, cambie `CButton` `CMFCColorPickerCtrl`el tipo de variable de a .

1. Inserte `WM_INITDIALOG` el controlador de mensajes para la clase de cuadro de diálogo. En el controlador, establezca el tipo, la `CMFCColorPickerCtrl` paleta y el color seleccionado inicial del control.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCColorPickerCtrl` muestra cómo configurar `CMFCColorPickerCtrl` un objeto mediante varios métodos en la clase. En el ejemplo se muestra cómo establecer el tipo del control de selector y cómo establecer su color, matiz, luminancia y saturación. El ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

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

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a>CMFCColorPickerCtrl::CMFCColorPickerCtrl

Construye un objeto `CMFCColorPickerCtrl`.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a>CMFCColorPickerCtrl::DrawCursor

Llamado por el marco de trabajo antes de un cursor que apunta al color seleccionado se muestra.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] Especifica un área rectangular alrededor del color seleccionado.

### <a name="remarks"></a>Observaciones

Invalide este método cuando necesite cambiar la forma del cursor que apunta al color seleccionado.

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a>CMFCColorPickerCtrl::GetColor

Recupera el color que selecciona el usuario.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El valor RGB del color seleccionado.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a>CMFCColorPickerCtrl::GetHLS

Recupera los valores de matiz, luminancia y saturación del color que el usuario selecciona.

```cpp
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Parámetros

*Hue*<br/>
[fuera] Puntero a una variable de tipo double que recibe información de matiz.

*Luminancia*<br/>
[fuera] Puntero a una variable de tipo double que recibe información de luminancia.

*Saturación*<br/>
[fuera] Puntero a una variable de tipo double que recibe información de saturación.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a>CMFCColorPickerCtrl::GetHue

Recupera el componente de matiz del color que selecciona el usuario.

```
double GetHue() const;
```

### <a name="return-value"></a>Valor devuelto

Componente de matiz del color seleccionado.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a>CMFCColorPickerCtrl::GetLuminance

Recupera el componente de luminancia del color que selecciona el usuario.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Valor devuelto

El componente de luminancia del color seleccionado.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a>CMFCColorPickerCtrl::GetSaturation

Recupera el valor de saturación del color que el usuario selecciona.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Valor devuelto

El componente de saturación del color seleccionado.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a>CMFCColorPickerCtrl::SelectCellHexagon

Establece el color actual en el color definido por los componentes de color RGB especificados o el hexágono de celda especificado.

```cpp
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
[en] El componente de color rojo.

*G*<br/>
[en] El componente de color verde.

*B*<br/>
[en] El componente de color azul.

*x*<br/>
[en] Coordenada x del cursor, que apunta a un hexágono de celda.

*y y*<br/>
[en] Coordenada y del cursor, que apunta a un hexágono de celda.

### <a name="return-value"></a>Valor devuelto

La segunda sobrecarga de este método siempre devuelve FALSE.

### <a name="remarks"></a>Observaciones

La primera sobrecarga de este método establece el color actual en el color que corresponde a los componentes de color rojo, verde y azul especificados del control de selección de color.

La segunda sobrecarga de este método establece el color actual en el color del hexágono de celda al que apunta la ubicación del cursor especificada.

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a>CMFCColorPickerCtrl::SetColor

Establece el color actual en el valor de color RGB especificado.

```cpp
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Un valor de color RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a>CMFCColorPickerCtrl::SetHLS

Establece el color actual en el valor de color HLS especificado.

```cpp
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Parámetros

*Hue*<br/>
[en] Un valor de matiz.

*Luminancia*<br/>
[en] Un valor de luminancia.

*Saturación*<br/>
[en] Un valor de saturación.

*bInvalidar*<br/>
[en] TRUE para forzar la ventana para actualizar inmediatamente al nuevo color; de lo contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a>CMFCColorPickerCtrl::SetHue

Cambia el tono del color seleccionado actualmente.

```cpp
void SetHue(double Hue);
```

### <a name="parameters"></a>Parámetros

*Hue*<br/>
[en] Un valor de matiz.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a>CMFCColorPickerCtrl::SetLuminance

Cambia la luminancia del color seleccionado actualmente.

```cpp
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Parámetros

*Luminancia*<br/>
[en] Un valor de luminancia.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a>CMFCColorPickerCtrl::SetLuminanceBarWidth

Establece el ancho de la barra de luminancia en el control de selector de color.

```cpp
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Parámetros

*w*<br/>
[en] El ancho de la barra de luminancia medida en píxeles.

### <a name="remarks"></a>Observaciones

Utilice este método para cambiar el tamaño de la barra de luminancia, que se encuentra en la ficha **Personalizado** del control selector de color. El parámetro *w* especifica el nuevo ancho de la barra de luminancia. El valor de ancho se omite si supera las tres cuartas partes del ancho del área de cliente.

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a>CMFCColorPickerCtrl::SetOriginalColor

Establece el color seleccionado inicialmente.

```cpp
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Parámetros

*ref*<br/>
[en] Un valor de color RGB.

### <a name="remarks"></a>Observaciones

Llame a este método cuando se inicializa el control selector de color.

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a>CMFCColorPickerCtrl::SetPalette

Establece la paleta de colores actual.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parámetros

*pPalette*<br/>
[en] Puntero a una paleta de colores.

### <a name="remarks"></a>Observaciones

La paleta de colores define la matriz de colores que se presenta en el control selector de color.

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a>CMFCColorPickerCtrl::SetSaturation

Cambia la saturación del color seleccionado actualmente.

```cpp
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Parámetros

*Saturación*<br/>
[en] Un valor de saturación.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a>CMFCColorPickerCtrl::SetType

Establece el tipo de control selector de color que se va a mostrar.

```cpp
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Parámetros

*colorType*<br/>
[en] Un tipo de control de selector de color.

Los tipos se `CMFCColorPickerCtrl::COLORTYPE` definen mediante la enumeración. Los tipos posibles son LUMINANCE, PICKER, HEX y HEX_GREYSCALE. El tipo predeterminado es PICKER.

### <a name="remarks"></a>Observaciones

Para especificar un tipo de control de selector de color, llame a este método antes de crear el control de Windows.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md)
