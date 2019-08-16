---
title: Clase CDrawingManager
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: 69365b66b12d5a9284c9b097b225ba041e07b6b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506805"
---
# <a name="cdrawingmanager-class"></a>Clase CDrawingManager

La `CDrawingManager` clase implementa algoritmos de dibujo complejos.

## <a name="syntax"></a>Sintaxis

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Construye un objeto `CDrawingManager`.|
|`CDrawingManager::~CDrawingManager`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Crea un mapa de bits independiente del dispositivo (DIB) de 32 bits en el que las aplicaciones pueden escribir directamente.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.|
|[CDrawingManager::DrawRotated](#drawrotated)|Gira el contenido de un controlador de dominio de origen dentro del rectángulo especificado por +/-90 grados|
|[CDrawingManager::DrawEllipse](#drawellipse)|Dibuja una elipse con los colores de relleno y borde proporcionados.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Dibuja un anillo y lo rellena con un degradado de color.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Dibuja una línea.|
|[CDrawingManager::DrawRect](#drawrect)|Dibuja un rectángulo con los colores de relleno y borde proporcionados.|
|[CDrawingManager::DrawShadow](#drawshadow)|Dibuja una sombra para un área rectangular.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Rellena un área rectangular con dos degradados de color.|
|[CDrawingManager::FillGradient](#fillgradient)|Rellena un área rectangular con un degradado de color especificado.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Rellena un área rectangular con un degradado de color especificado. También se especifica la dirección del cambio de color del degradado.|
|[CDrawingManager::GrayRect](#grayrect)|Rellena un rectángulo con un color gris especificado.|
|[CDrawingManager::HighlightRect](#highlightrect)|Resalta un área rectangular.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Convierte un color de una representación HLS en una representación RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Convierte un color de una representación HLS en una representación RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Convierte un color de una representación HSV en una representación RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Método auxiliar que convierte un valor de matiz en un componente rojo, verde o azul.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Voltea un área rectangular.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Método auxiliar que determina el color final de un píxel semitransparente.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Crea un mapa de bits que se puede utilizar como sombra.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convierte un color de una representación RGB en una representación HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convierte un color de una representación RGB en una representación HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Método auxiliar que colorea un píxel parcialmente transparente en un mapa de bits.|
|[CDrawingManager::SetPixel](#setpixel)|Método auxiliar que cambia un solo píxel de un mapa de bits al color especificado.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combina dos colores en función de una relación ponderada.|

## <a name="remarks"></a>Comentarios

La `CDrawingManager` clase proporciona funciones para dibujar sombras, degradados de color y rectángulos resaltados. También realiza la combinación alfa. Puede usar esta clase para cambiar directamente la interfaz de usuario de la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdrawmanager. h

##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

Construye un objeto [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) .

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
de Referencia a un contexto de dispositivo. `CDrawingManager` Utiliza este contexto para dibujar.

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

Crea un mapa de bits independiente del dispositivo (DIB) de 32 bits en el que las aplicaciones pueden escribir directamente.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|DESCRIPCIÓN|
|*size*|de Un parámetro [CSize](../../atl-mfc-shared/reference/csize-class.md) que indica el tamaño del mapa de bits.|
|*pBits*|enuncia Un puntero a un puntero de datos que recibe la ubicación de los valores de bit del DIB.|
|*bitmap*|Identificador del mapa de bits original|
|*clrTransparent*|Valor RGB que especifica el color transparente del mapa de bits original.|

### <a name="return-value"></a>Valor devuelto

Identificador del mapa de bits DIB recién creado si este método se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre cómo crear un mapa de bits DIB, vea [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parámetros

*pDstDC*<br/>
de Un puntero al contexto de dispositivo para el destino.

*rectDst*<br/>
de Rectángulo de destino.

*pSrcDC*<br/>
de Un puntero al contexto de dispositivo para el origen.

*rectSrc*<br/>
de Rectángulo de origen.

### <a name="remarks"></a>Comentarios

Este método realiza la combinación alfa para dos mapas de bits. Para obtener más información sobre la combinación alfa, vea [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) en el Windows SDK.

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

Dibuja una elipse con los colores de relleno y borde proporcionados.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Rectángulo delimitador de la elipse.

*clrFill*<br/>
de Color que usa este método para rellenar la elipse.

*clrLine*<br/>
de Color que usa este método como borde de la elipse.

### <a name="remarks"></a>Comentarios

Este método devuelve sin dibujar una elipse si cualquiera de los colores está establecido en-1. También devuelve sin dibujar una elipse si cualquiera de las dimensiones del rectángulo delimitador es 0.

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

Dibuja un anillo y lo rellena con un degradado de color.

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Un parámetro [CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica el límite para el anillo de degradado.

*colorStart*<br/>
de Primer color del degradado.

*colorFinish*<br/>
de Último color del degradado.

*colorBorder*<br/>
de Color del borde.

*nAngle*<br/>
de Parámetro que especifica el ángulo de dibujo del degradado inicial. Este valor debe estar comprendido entre 0 y 360.

*nWidth*<br/>
de Ancho del borde del anillo.

*clrFace*<br/>
de Color del interior del anillo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El rectángulo definido por *Rect* debe tener al menos 5 píxeles de ancho y 5 píxeles de alto.

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Dibuja una línea.

```
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|DESCRIPCIÓN|
|*x1*|de Coordenada x donde empieza la línea.|
|*y1*|de Coordenada y en la que comienza la línea.|
|*x2*|de Coordenada x donde finaliza la línea.|
|*y2*|de Coordenada y donde finaliza la línea.|
|*clrLine*|de Color de la línea.|

### <a name="remarks"></a>Comentarios

Este método produce un error si *clrLine* es igual a-1.

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

Dibuja un rectángulo con los colores de relleno y borde proporcionados.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Los límites del rectángulo.

*clrFill*<br/>
de Color que usa este método para rellenar el rectángulo.

*clrLine*<br/>
de Color que usa este método para el borde del rectángulo.

### <a name="remarks"></a>Comentarios

Este método devuelve sin dibujar un rectángulo si cualquiera de los colores está establecido en-1. También devuelve si cualquiera de las dimensiones del rectángulo es 0.

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

Dibuja una sombra para un área rectangular.

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Área rectangular de la aplicación. El administrador de dibujos dibujará una sombra debajo de esta área.

*nDepth*<br/>
de Ancho y alto de la sombra.

*iMinBrightness*<br/>
de Brillo mínimo de la sombra.

*iMaxBrightness*<br/>
de Brillo máximo de la sombra.

*pBmpSaveBottom*<br/>
de Un puntero a un mapa de bits que contiene la imagen de la parte inferior de la sombra.

*pBmpSaveRight*<br/>
de Un puntero a un mapa de bits que contiene la imagen de la sombra que se dibuja en el lado derecho del rectángulo.

*clrBase*<br/>
de Color de la sombra.

*bRightShadow*<br/>
de Un parámetro booleano que indica cómo se dibuja la sombra. Si *bRightShadow* es `TRUE`, `DrawShadow` dibuja una sombra en el lado derecho del rectángulo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Puede proporcionar dos mapas de bits válidos para las sombras inferior y derecha mediante los parámetros *pBmpSaveBottom* y *pBmpSaveRight*. Si estos objetos [CBitmap](../../mfc/reference/cbitmap-class.md) tienen un objeto GDI adjunto, `DrawShadow` usará esos mapas de bits como las sombras. Si los `CBitmap` parámetros no tienen un objeto GDI asociado, `DrawShadow` dibuja la sombra y adjunta los mapas de bits a los parámetros. En futuras llamadas a `DrawShadow`, puede proporcionar estos mapas de bits para acelerar el proceso de dibujo. Para obtener más información sobre `CBitmap` la clase y los objetos GDI, vea [objetos gráficos](../../mfc/graphic-objects.md).

Si alguno de estos parámetros es `NULL`, `DrawShadow` dibujará automáticamente la sombra.

Si establece *bRightShadow* en false, la sombra se dibujará debajo y a la izquierda del área rectangular.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `DrawShadow` el método de `CDrawingManager` la clase. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de la hoja de propiedades.

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

Rellena un área rectangular con dos degradados de color.

```
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Rectángulo que se va a rellenar.

*colorStart1*<br/>
de Color inicial del primer degradado de color.

*colorFinish1*<br/>
de Color final del primer degradado de color.

*colorStart2*<br/>
de Color inicial del segundo degradado de color.

*colorFinish2*<br/>
de Color final del segundo degradado de color.

*bHorz*<br/>
de Un parámetro booleano que indica si `Fill4ColorsGradient` los colores tienen un degradado horizontal o vertical. TRUE indica un degradado horizontal.

*nPercentage*<br/>
de Entero de 0-100. Este valor indica el porcentaje del rectángulo que se va a rellenar con el primer degradado de color.

### <a name="remarks"></a>Comentarios

Cuando un rectángulo se rellena con dos degradados de color, se colocan por encima o junto al otro, dependiendo del valor de *bHorz*. Cada degradado de color se calcula de forma independiente con el método [CDrawingManager:: FillGradient](#fillgradient).

Este método genera un error de aserción si *nPercentage* es menor que 0 o mayor que 100.

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

Rellena un área rectangular con el degradado de color especificado.

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Área rectangular que se va a rellenar.

*colorStart*<br/>
de Primer color del degradado.

*colorFinish*<br/>
de Color final del degradado.

*bHorz*<br/>
de Un parámetro booleano que especifica si `FillGradient` debe dibujar un degradado horizontal o vertical.

*nStartFlatPercentage*<br/>
de Porcentaje del rectángulo que `FillGradient` se llena con *colorStart* antes de iniciar el degradado.

*nEndFlatPercentage*<br/>
de Porcentaje del rectángulo que `FillGradient` se llena con *colorFinish* una vez finalizado el degradado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `FillGradient` el método de `CDrawingManager` la clase. Este fragmento de código forma parte del [ejemplo de demostración de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

Rellena un área rectangular con un degradado de color especificado.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Área rectangular que se va a rellenar.

*colorStart*<br/>
de Primer color del degradado.

*colorFinish*<br/>
de Último color del degradado.

*nAngle*<br/>
de Un entero entre 0 y 360. Este parámetro especifica la dirección del degradado de color.

### <a name="remarks"></a>Comentarios

Use *nAngle* para especificar la dirección del degradado de color. Cuando se especifica la dirección del degradado de color, también se especifica dónde se inicia el degradado de color. Un valor de 0 para *nAngle* indica que el degradado comienza en la parte superior del rectángulo. A medida que aumenta la *nAngle* , la ubicación inicial del degradado se mueve en sentido contrario a las agujas del reloj según el ángulo.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `FillGradient2` el método de `CDrawingManager` la clase. Este fragmento de código forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>  CDrawingManager::GrayRect

Rellena un rectángulo con un color gris especificado.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Área rectangular que se va a rellenar.

*nPercentage*<br/>
de Porcentaje de gris que se desea incluir en el rectángulo.

*clrTransparent*<br/>
de Color transparente.

*clrDisabled*<br/>
de Color que usa este método para la dessaturación si *nPercentage* está establecido en-1.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

En el caso del parámetro *nPercentage*, un valor inferior indica un color más oscuro.

El valor máximo de *nPercentage* es 200. Un valor mayor que 200 no cambia la apariencia del rectángulo. Si el valor es-1, este método usa *clrDisabled* para limitar la saturación del rectángulo.

##  <a name="highlightrect"></a>  CDrawingManager::HighlightRect

Resalta un área rectangular.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Área rectangular que se va a resaltar.

*nPercentage*<br/>
de Porcentaje que indica la transparencia que debe tener el resaltado.

*clrTransparent*<br/>
de Color transparente.

*nTolerance*<br/>
de Entero comprendido entre 0 y 255 que indica la tolerancia de color.

*clrBlend*<br/>
de Color base de la fusión.

### <a name="return-value"></a>Valor devuelto

TRUE si el método es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si *nPercentage* se encuentra entre 0 y 99 `HighlightRect` , utiliza el algoritmo de combinación alfa. Para obtener más información sobre la combinación alfa, vea [líneas y rellenos de mezcla alfa](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si *nPercentage* es-1, este método usa el nivel de resaltado predeterminado. Si *nPercentage* es 100, este método no hace nada y devuelve true.

El método usa el parámetro *nTolerance* para determinar si se debe resaltar el área rectangular. Para resaltar el rectángulo, la diferencia entre el color de fondo de la aplicación y *clrTransparent* debe ser menor que *nTolerance* en cada componente de color (rojo, verde y azul).

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

Convierte un color de una representación HLS en una representación RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
de Número comprendido entre 0 y 1 que representa el matiz del color.

*L*<br/>
de Número comprendido entre 0 y 1 que indica la luminosidad del color.

*S*<br/>
de Número comprendido entre 0 y 1 que indica la saturación del color.

### <a name="return-value"></a>Valor devuelto

Representación RGB del color HLS proporcionado.

### <a name="remarks"></a>Comentarios

Un color se puede representar como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las distintas representaciones de color, vea [color](/windows/win32/uxguide/vis-color).

Este método y el `CDrawingManager::HLStoRGB_TWO` método realizan la misma operación, pero requieren valores diferentes para el parámetro *H* . En este método, *H* es un porcentaje del círculo. En el `CDrawingManager::HLStoRGB_TWO` método, *H* es un valor de degree entre 0 y 360, que representan rojo. Por ejemplo, con `HLStoRGB_ONE`, un valor de 0,25 para *H* es equivalente a un valor de 90 con `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

Convierte un color de una representación HLS en una representación RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
de Número comprendido entre 0 y 360 que representa el matiz del color.

*L*<br/>
de Número comprendido entre 0 y 1 que indica la luminosidad del color.

*S*<br/>
de Número comprendido entre 0 y 1 que indica la saturación del color.

### <a name="return-value"></a>Valor devuelto

Representación RGB del color HLS proporcionado.

### <a name="remarks"></a>Comentarios

Un color se puede representar como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las distintas representaciones de color, vea [color](/windows/win32/uxguide/vis-color).

Este método y el método [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) realizan la misma operación, pero requieren valores diferentes para el parámetro *H* . En este método, *H* es un valor de degree entre 0 y 360, que representan rojo. En el método [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) , *H* es un porcentaje del círculo. Por ejemplo, con `HLStoRGB_ONE`, un valor de 0,25 para *H* es equivalente a un valor de 90 con `HLStoRGB_TWO`.

##  <a name="hsvtorgb"></a>  CDrawingManager::HSVtoRGB

Convierte un color de una representación HSV en una representación RGB.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|DESCRIPCIÓN|
|*H*|de Número comprendido entre 0 y 360 que indica el matiz del color.|
|*S*|de Número comprendido entre 0 y 1 que indica la saturación del color.|
|*V*|de Número comprendido entre 0 y 1 que indica el valor del color.|

### <a name="return-value"></a>Valor devuelto

Representación RGB del color HSV proporcionado.

### <a name="remarks"></a>Comentarios

Un color se puede representar como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las distintas representaciones de color, vea [color](/windows/win32/uxguide/vis-color).

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

Convierte un valor de matiz en un componente rojo, verde o azul.

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>Parámetros

*m1*<br/>
de Vea la sección Comentarios.

*m2*<br/>
de Vea la sección Comentarios.

*h*<br/>
de Vea la sección Comentarios.

*rm1*<br/>
de Vea la sección Comentarios.

*rm2*<br/>
de Vea la sección Comentarios.

*rh*<br/>
de Vea la sección Comentarios.

### <a name="return-value"></a>Valor devuelto

Componente individual rojo, verde o azul del matiz proporcionado.

### <a name="remarks"></a>Comentarios

Este método es un método auxiliar que la `CDrawingManager` clase utiliza para calcular los componentes individuales rojo, verde y azul de un color en una representación HSV o HSL. Este método no está diseñado para ser llamado directamente por el programador. Los parámetros de entrada son valores que dependen del algoritmo de conversión.

Para convertir un color HSV o HSL en una representación RGB, llame a uno de los métodos siguientes:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect

Voltea un área rectangular.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Rectángulo delimitador del área que se va a voltear.

*bHorz*<br/>
de Un parámetro booleano que indica si el rectángulo se voltea horizontal o verticalmente.

### <a name="remarks"></a>Comentarios

Este método puede voltear cualquier área del contexto de dispositivo que pertenezca `CDrawingManager` a la clase. Si *bHorz* se establece en true, este método voltea el área horizontalmente. De lo contrario, voltea el área verticalmente.

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

Calcula el color final de un píxel semitransparente.

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>Parámetros

*srcPixel*<br/>
de Color inicial del píxel.

*percent*<br/>
de Número comprendido entre 0 y 100 que representa el porcentaje de transparencia. Un valor de 100 indica que el color inicial es completamente transparente.

*percentR*<br/>
de Número comprendido entre 0 y 100 que representa el porcentaje de transparencia del componente rojo.

*percentG*<br/>
de Número comprendido entre 0 y 100 que representa el porcentaje de transparencia del componente verde.

*percentB*<br/>
de Número comprendido entre 0 y 100 que representa el porcentaje de transparencia del componente azul.

*dstPixel*<br/>
de Color base del píxel.

### <a name="return-value"></a>Valor devuelto

Color final del píxel semitransparente.

### <a name="remarks"></a>Comentarios

Se trata de una clase auxiliar para colorear mapas de bits semitransparentes y no está diseñada para ser llamada directamente por el programador.

Cuando se usa la versión del método que tiene *dstPixel*, el color final es una combinación de *dstPixel* y *srcPixel*. El color *srcPixel* es el color parcialmente transparente sobre el color base de *dstPixel*.

##  <a name="prepareshadowmask"></a>CDrawingManager::P repareShadowMask

Crea un mapa de bits que se puede utilizar como sombra.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parámetros

*nDepth*<br/>
de Ancho y alto de la sombra.

*clrBase*<br/>
de Color de la sombra.

*iMinBrightness*<br/>
de Brillo mínimo de la sombra.

*iMaxBrightness*<br/>
de Brillo máximo de la sombra.

### <a name="return-value"></a>Valor devuelto

Identificador del mapa de bits creado si este método se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si *nDepth* se establece en 0, este método sale y devuelve NULL. Si *nDepth* es menor que 3, el ancho y el alto de la sombra se establecen en 3 píxeles.

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

Convierte un color de una representación roja, verde y azul (RGB) en una representación de matiz, saturación y luminosidad (HSL).

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|DESCRIPCIÓN|
|*rgb*|de Color en valores RGB.|
|*H*|enuncia Un puntero a un valor Double donde el método almacena el matiz del color.|
|*S*|enuncia Un puntero a un valor Double donde el método almacena la saturación del color.|
|*L*|enuncia Puntero a un valor Double donde el método almacena la luminosidad del color.|

### <a name="remarks"></a>Comentarios

Un color se puede representar como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las distintas representaciones de color, vea [color](/windows/win32/uxguide/vis-color).

El valor devuelto para *H* se representa como una fracción entre 0 y 1, donde 0 y 1 representan rojo. Los valores devueltos para *S* y *L* son números entre 0 y 1.

##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV

Convierte un color de una representación RGB en una representación HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parámetros

*rgb*<br/>
de Color que se va a convertir en una representación RGB.

*H*<br/>
enuncia Un puntero a un valor Double donde este método almacena el matiz resultante para el color.

*S*<br/>
enuncia Un puntero a un valor Double donde este método almacena la saturación resultante del color.

*V*<br/>
enuncia Un puntero a un valor Double donde este método almacena el valor resultante para el color.

### <a name="remarks"></a>Comentarios

Un color se puede representar como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las distintas representaciones de color, vea [color](/windows/win32/uxguide/vis-color).

El valor devuelto para *H* es un número comprendido entre 0 y 360, donde 0 y 360 indican rojo. Los valores devueltos para *S* y *V* son números entre 0 y 1.

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

Colorea un píxel transparente en un mapa de bits.

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>Parámetros

*pBits*<br/>
de Puntero a los valores de bit para el mapa de bits.

*rect*<br/>
de Área rectangular de la aplicación. El administrador de dibujos dibuja una sombra debajo y a la derecha de esta área.

*x*<br/>
de Coordenada horizontal del píxel que se va a colorear.

*y*<br/>
de Coordenada vertical del píxel que se va a colorear.

*percent*<br/>
de Porcentaje de transparencia.

*iShadowSize*<br/>
de Ancho y alto de la sombra.

*clrBase*<br/>
de Color de la sombra.

*bIsRight*<br/>
de Parámetro booleano que indica en qué píxel se va a colorear. Vea la sección Comentarios para obtener más información.

### <a name="remarks"></a>Comentarios

Este método es un método auxiliar que usa el método [CDrawingManager::D rawshadow](#drawshadow) . Se recomienda que, si desea dibujar una sombra, llame a `CDrawingManager::DrawShadow` en su lugar.

Si *bIsRight* se establece en true, el píxel al color se mide *x* píxeles desde el borde derecho de *Rect*. Si es FALSE, el píxel al color se mide *x* píxeles desde el borde izquierdo de *Rect*.

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

Cambia un solo píxel de un mapa de bits al color especificado.

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|DESCRIPCIÓN|
|*pBits*|de Puntero a los valores de bit del mapa de bits.|
|*cx*|de Ancho total del mapa de bits.|
|*cy*|de Alto total del mapa de bits.|
|*x*|de Coordenada x del píxel del mapa de bits que se va a cambiar.|
|*y*|de Coordenada y del píxel del mapa de bits que se va a cambiar.|
|*color*|de Nuevo color del píxel identificado por las coordenadas proporcionadas.|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

Combina dos colores en función de una relación ponderada.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|DESCRIPCIÓN|
|*color1*|de Primer color que se va a mezclar.|
|*color2*|de Segundo color que se va a mezclar.|
|*dblLumRatio*|de La proporción de la luminosidad del nuevo color. `SmartMixColors`multiplica la luminosidad del color mezclado por esta relación antes de determinar el color final.|
|*k1*|de La proporción ponderada para el primer color.|
|*k2*|de La proporción ponderada para el segundo color.|

### <a name="return-value"></a>Valor devuelto

Color que representa una mezcla ponderada de los colores proporcionados.

### <a name="remarks"></a>Comentarios

Este método produce un error si *K1* o *K2* es menor que cero. Si ambos parámetros se establecen en 0, el método devuelve `RGB(0, 0, 0)`.

La relación ponderada se calcula con la fórmula siguiente: (color1 \* K1 + color2 \* K2)/(K1 + K2). Una vez determinada la relación ponderada, el método calcula la luminosidad del color mixto. A continuación, multiplica la luminosidad por *dblLumRatio*. Si el valor es mayor que 1,0, el método establece la luminosidad del color mezclado en el nuevo valor. De lo contrario, la luminosidad se establece en 1,0.

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

Gira el contenido de un controlador de dominio de origen dentro del rectángulo dado en 90 grados.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parámetros

*rectDest*<br/>
Rectángulo de destino.

*dcSrc*<br/>
Contexto de dispositivo de origen.

*bClockWise*<br/>
TRUE indica girar + 90 grados; FALSE indica Rotate-90 grados.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
