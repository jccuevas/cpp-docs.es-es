---
title: CDrawingManager (clase)
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
ms.openlocfilehash: 506ab7a06653942ecff05043a7e7efabd535115f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781697"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager (clase)

La `CDrawingManager` clase implementa los algoritmos de dibujos complejos.

## <a name="syntax"></a>Sintaxis

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Construye un objeto `CDrawingManager`.|
|`CDrawingManager::~CDrawingManager`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Crea un mapa de bits de 32 bits de independientes del dispositivo (DIB) que las aplicaciones pueden escribir directamente.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Muestra los mapas de bits con píxeles transparentes o semitransparentes.|
|[CDrawingManager::DrawRotated](#drawrotated)|Gira un origen de contenido de los DC dentro del rectángulo especificado por +/-90 grados|
|[CDrawingManager::DrawEllipse](#drawellipse)|Dibuja una elipse con los colores de relleno y borde proporcionados.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Dibuja un anillo y lo rellena con un degradado de color.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Dibuja una línea.|
|[CDrawingManager::DrawRect](#drawrect)|Dibuja un rectángulo con el color de relleno y borde proporcionado.|
|[CDrawingManager::DrawShadow](#drawshadow)|Dibuja una sombra de un área rectangular.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Rellena un área rectangular con dos degradados de color.|
|[CDrawingManager::FillGradient](#fillgradient)|Rellena un área rectangular con un degradado de color especificado.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Rellena un área rectangular con un degradado de color especificado. También se especifica la dirección del cambio de color del degradado.|
|[CDrawingManager::GrayRect](#grayrect)|Rellena un rectángulo con un color gris especificado.|
|[CDrawingManager::HighlightRect](#highlightrect)|Resalta un área rectangular.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Convierte un color de una representación de HLS en una representación RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Convierte un color de una representación de HLS en una representación RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Convierte un color de una representación HSV en una representación RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Método auxiliar que convierte un valor de hue en un componente rojo, verde o azul.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Voltea un área rectangular.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Método auxiliar que determina el color final de un píxel semitransparente.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Crea un mapa de bits que se puede usar como una sombra.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convierte un color de una representación RGB en una representación HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convierte un color de una representación RGB en una representación HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Método auxiliar que los colores de un píxel parcialmente transparente en un mapa de bits.|
|[CDrawingManager::SetPixel](#setpixel)|Método auxiliar que cambia de un solo píxel en un mapa de bits en el color especificado.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combina dos colores según una proporción ponderada.|

## <a name="remarks"></a>Comentarios

La `CDrawingManager` clase proporciona funciones para dibujar sombras, degradados de color y rectángulos resaltados. También realiza la combinación alfa. Puede usar esta clase para cambiar directamente la interfaz de usuario de la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdrawmanager.h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

Construye un [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) objeto.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
[in] Una referencia a un contexto de dispositivo. El `CDrawingManager` este contexto se utiliza para dibujar.

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

Crea un mapa de bits de 32 bits de independientes del dispositivo (DIB) que las aplicaciones pueden escribir directamente.

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
|Parámetro|Descripción|
|*size*|[in] Un [CSize](../../atl-mfc-shared/reference/csize-class.md) parámetro que indica el tamaño del mapa de bits.|
|*pBits*|[out] Un puntero a un puntero de datos que recibe la ubicación de la imagen de DIB valores de bit.|
|*bitmap*|Un identificador para el mapa de bits original|
|*clrTransparent*|Un valor RGB especificando un color transparente del mapa de bits original.|

### <a name="return-value"></a>Valor devuelto

Un identificador para el mapa de bits DIB recién creado si este método se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre cómo crear un mapa de bits DIB, consulte [CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

Muestra los mapas de bits con píxeles transparentes o semitransparentes.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parámetros

*pDstDC*<br/>
[in] Un puntero al contexto de dispositivo para el destino.

*rectDst*<br/>
[in] El rectángulo de destino.

*pSrcDC*<br/>
[in] Un puntero al contexto de dispositivo para el origen.

*rectSrc*<br/>
[in] El rectángulo de origen.

### <a name="remarks"></a>Comentarios

Este método realiza la combinación alfa para dos mapas de bits. Para obtener más información acerca de la combinación alfa, consulte [AlphaBlend](/windows/desktop/api/wingdi/nf-wingdi-alphablend) en el SDK de Windows.

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
[in] El rectángulo delimitador de la elipse.

*clrFill*<br/>
[in] El color de que este método se utiliza para rellenar la elipse.

*clrLine*<br/>
[in] El color de este método se utiliza como el borde de la elipse.

### <a name="remarks"></a>Comentarios

Este método devuelve sin dibujar una elipse si uno de los colores se establece en -1. También se devuelve sin dibujar una elipse si ambas dimensiones del rectángulo delimitador es 0.

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
[in] Un [CRect](../../atl-mfc-shared/reference/crect-class.md) parámetro que especifica el límite para el anillo de degradado.

*colorStart*<br/>
[in] El primer color del degradado.

*colorFinish*<br/>
[in] El último color para el degradado.

*colorBorder*<br/>
[in] El color del borde.

*nAngle*<br/>
[in] Un parámetro que especifica el ángulo inicial de dibujo degradado. Este valor debe estar entre 0 y 360.

*nWidth*<br/>
[in] El ancho del borde para el anillo.

*clrFace*<br/>
[in] El color del interior del anillo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El rectángulo definido por *rect* deben ser al menos 5 píxeles de anchos y 5 píxeles de alto.

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
|Parámetro|Descripción|
|*x1*|[in] La coordenada x donde comienza la línea.|
|*y1*|[in] Coordenada y donde comienza la línea.|
|*x2*|[in] La coordenada x donde finaliza la línea.|
|*y2*|[in] Coordenada y donde finaliza la línea.|
|*clrLine*|[in] El color de la línea.|

### <a name="remarks"></a>Comentarios

Este método produce un error si *clrLine* es igual a -1.

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

Dibuja un rectángulo con el color de relleno y borde proporcionado.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
[in] Los límites del rectángulo.

*clrFill*<br/>
[in] El color de que este método se usa para rellenar el rectángulo.

*clrLine*<br/>
[in] El color de este método se utiliza para el borde del rectángulo.

### <a name="remarks"></a>Comentarios

Este método devuelve sin dibujar un rectángulo si uno de los colores se establece en -1. También devuelve si ambas dimensiones del rectángulo es 0.

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

Dibuja una sombra de un área rectangular.

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
[in] Un área rectangular en la aplicación. El Administrador de dibujo dibujará una sombra debajo de esta área.

*nDepth*<br/>
[in] El ancho y alto de la sombra.

*iMinBrightness*<br/>
[in] El brillo mínimo de la sombra.

*iMaxBrightness*<br/>
[in] El brillo máximo de la sombra.

*pBmpSaveBottom*<br/>
[in] Un puntero a un mapa de bits que contiene la imagen de la parte inferior de la sombra.

*pBmpSaveRight*<br/>
[in] Un puntero a un mapa de bits que contiene la imagen de la sombra que se dibuja en el lado derecho del rectángulo.

*clrBase*<br/>
[in] El color de la sombra.

*bRightShadow*<br/>
[in] Un parámetro booleano que indica cómo se dibuja la sombra. Si *bRightShadow* es `TRUE`, `DrawShadow` dibuja una sombra en el lado derecho del rectángulo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Puede proporcionar dos mapas de bits válidos para la parte inferior y derechos sombras mediante los parámetros *pBmpSaveBottom* y *pBmpSaveRight*. Si estos [CBitmap](../../mfc/reference/cbitmap-class.md) objetos tienen un objeto GDI adjunto, `DrawShadow` va a usar los mapas de bits como las sombras. Si el `CBitmap` parámetros no tienen un objeto GDI adjunto, `DrawShadow` dibuja la sombra y adjunta los mapas de bits a los parámetros. En futuras llamadas a `DrawShadow`, puede proporcionar estos mapas de bits para acelerar el proceso de dibujo. Para obtener más información sobre la `CBitmap` clase y objetos GDI, vea [objetos gráficos](../../mfc/graphic-objects.md).

Si alguno de estos parámetros es `NULL`, `DrawShadow` automáticamente se dibujará la sombra.

Si establece *bRightShadow* en FALSE, se dibujará la sombra debajo y a la izquierda del área rectangular.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `DrawShadow` método de la `CDrawingManager` clase. Este fragmento de código forma parte de la [ejemplo de demostración de hoja Prop](../../overview/visual-cpp-samples.md).

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
[in] Para rellenar el rectángulo.

*colorStart1*<br/>
[in] Color inicial del degradado de color de primer.

*colorFinish1*<br/>
[in] Color final del degradado de color de primer.

*colorStart2*<br/>
[in] Color inicial del degradado de color de segundo.

*colorFinish2*<br/>
[in] Color final del degradado de color de segundo.

*bHorz*<br/>
[in] Un parámetro booleano que indica si `Fill4ColorsGradient` colores de un degradado horizontal o vertical. TRUE indica que un degradado horizontal.

*nPercentage*<br/>
[in] Un entero entre 0 y 100. Este valor indica el porcentaje del rectángulo que se rellena con el primer degradado de color.

### <a name="remarks"></a>Comentarios

Cuando un rectángulo se rellena con dos degradados de color, son encuentra anteriormente entre sí o junto a otro, dependiendo del valor de *bHorz*. Cada degradado de color se calcula de forma independiente con el método [CDrawingManager::FillGradient](#fillgradient).

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
[in] El área rectangular a rellenar.

*colorStart*<br/>
[in] El primer color del degradado.

*colorFinish*<br/>
[in] El color final del degradado.

*bHorz*<br/>
[in] Un parámetro booleano que especifica si `FillGradient` debe dibujar un degradado horizontal o vertical.

*nStartFlatPercentage*<br/>
[in] El porcentaje del rectángulo que `FillGradient` rellena con *colorStart* antes de que comience el degradado.

*nEndFlatPercentage*<br/>
[in] El porcentaje del rectángulo que `FillGradient` rellena con *colorFinish* cuando finaliza el degradado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `FillGradient` método de la `CDrawingManager` clase. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../overview/visual-cpp-samples.md).

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
[in] El área rectangular a rellenar.

*colorStart*<br/>
[in] El primer color del degradado.

*colorFinish*<br/>
[in] El último color del degradado.

*nAngle*<br/>
[in] Un entero entre 0 y 360. Este parámetro especifica la dirección del degradado de color.

### <a name="remarks"></a>Comentarios

Use *nAngle* para especificar la dirección del degradado de color. Cuando se especifica la dirección del degradado de color, también especificar donde comienza el degradado de color. Un valor de 0 para *nAngle* indica el degradado se inicia desde la parte superior del rectángulo. Como *nAngle* aumenta, la ubicación de inicio para el degradado se mueve en una dirección hacia la izquierda según el ángulo.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `FillGradient2` método de la `CDrawingManager` clase. Este fragmento de código forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

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
[in] El área rectangular a rellenar.

*nPercentage*<br/>
[in] El porcentaje de color gris que desee en el rectángulo.

*clrTransparent*<br/>
[in] Color transparente.

*clrDisabled*<br/>
[in] El color que utiliza este método para la saturación si *nPercentage* se establece en -1.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para el parámetro *nPercentage*, un valor inferior indica un color más oscuro.

El valor máximo de *nPercentage* es 200. Un valor mayor que 200 no cambia la apariencia del rectángulo. Si el valor es -1, este método usa *clrDisabled* para limitar la saturación del rectángulo.

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
[in] Un área rectangular a resaltar.

*nPercentage*<br/>
[in] Un porcentaje que indica cómo transparente debe ser el resaltado.

*clrTransparent*<br/>
[in] Color transparente.

*nTolerance*<br/>
[in] Un entero entre 0 y 255 que indica la tolerancia de color.

*clrBlend*<br/>
[in] El color de la base de fusión.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si *nPercentage* está comprendido entre 0 y 99, `HighlightRect` utiliza el algoritmo de combinación de alfa. Para obtener más información acerca de la combinación alfa, consulte [Alpha Blending líneas y rellenos](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si *nPercentage* es -1, este método utiliza el nivel de resaltado predeterminado. Si *nPercentage* es 100, este método no hace nada y devuelve TRUE.

El método usa el parámetro *nTolerance* para determinar si desea resaltar el área rectangular. Para resaltar el rectángulo, la diferencia entre el color de fondo de la aplicación y *clrTransparent* debe ser menor que *nTolerance* en cada componente de color (rojo, verde y azul).

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

Convierte un color de una representación de HLS en una representación RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
[in] Un número entre 0 y 1 que representa el matiz del color.

*L*<br/>
[in] Un número entre 0 y 1 que indica la luminosidad del color.

*S*<br/>
[in] Un número entre 0 y 1 que indica la saturación del color.

### <a name="return-value"></a>Valor devuelto

La representación RGB del color HLS proporcionado.

### <a name="remarks"></a>Comentarios

Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](/windows/desktop/uxguide/vis-color).

Este método y el `CDrawingManager::HLStoRGB_TWO` método realiza la misma operación, pero requieren valores diferentes para el *H* parámetro. En este método, *H* es un porcentaje del círculo. En el `CDrawingManager::HLStoRGB_TWO` método *H* es un valor de grado, entre 0 y 360, que representan el rojo. Por ejemplo, con `HLStoRGB_ONE`, un valor de 0,25 para *H* es equivalente a un valor de 90 con `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

Convierte un color de una representación de HLS en una representación RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
[in] Un número entre 0 y 360, que representa el matiz del color.

*L*<br/>
[in] Un número entre 0 y 1 que indica la luminosidad del color.

*S*<br/>
[in] Un número entre 0 y 1 que indica la saturación del color.

### <a name="return-value"></a>Valor devuelto

La representación RGB del color HLS proporcionado.

### <a name="remarks"></a>Comentarios

Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](/windows/desktop/uxguide/vis-color).

Este método y el [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) método realiza la misma operación, pero requieren valores diferentes para el *H* parámetro. En este método, *H* es un valor de grado, entre 0 y 360, que representan el rojo. En el [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) método *H* es un porcentaje del círculo. Por ejemplo, con `HLStoRGB_ONE`, un valor de 0,25 para *H* es equivalente a un valor de 90 con `HLStoRGB_TWO`.

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
|Parámetro|Descripción|
|*H*|[in] Un número entre 0 y 360, que indica el matiz del color.|
|*S*|[in] Un número entre 0 y 1 que indica la saturación del color.|
|*V*|[in] Un número entre 0 y 1 que indica el valor del color.|

### <a name="return-value"></a>Valor devuelto

La representación RGB del color HSV proporcionado.

### <a name="remarks"></a>Comentarios

Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](/windows/desktop/uxguide/vis-color).

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

Convierte un valor de hue en un componente rojo, verde o azul.

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
[in] Vea la sección Comentarios.

*m2*<br/>
[in] Vea la sección Comentarios.

*h*<br/>
[in] Vea la sección Comentarios.

*rm1*<br/>
[in] Vea la sección Comentarios.

*rm2*<br/>
[in] Vea la sección Comentarios.

*rh*<br/>
[in] Vea la sección Comentarios.

### <a name="return-value"></a>Valor devuelto

El componente rojo, verde o azul individual para el matiz proporcionado.

### <a name="remarks"></a>Comentarios

Este método es un método auxiliar que el `CDrawingManager` clase utiliza para calcular los componentes rojos, verde y azules individuales de un color en una representación HSV o HSL. Este método no está diseñado para ser llamado directamente por el programador. Los parámetros de entrada son valores que dependen del algoritmo de conversión.

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
[in] El rectángulo delimitador del área para voltear.

*bHorz*<br/>
[in] Un parámetro booleano que indica si el rectángulo se voltea horizontalmente o verticalmente.

### <a name="remarks"></a>Comentarios

Este método puede voltear cualquier área del contexto del dispositivo que pertenecen a la `CDrawingManager` clase. Si *bHorz* está establecida en TRUE, este método invierte el área horizontalmente. En caso contrario, voltea el área verticalmente.

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
[in] Color inicial del píxel.

*percent*<br/>
[in] Un número entre 0 y 100 que representa el porcentaje de transparencia. Un valor de 100 indica que el color inicial es completamente transparente.

*percentR*<br/>
[in] Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente rojo.

*percentG*<br/>
[in] Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente verde.

*percentB*<br/>
[in] Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente azul.

*dstPixel*<br/>
[in] El color base del píxel.

### <a name="return-value"></a>Valor devuelto

El color final del píxel semitransparente.

### <a name="remarks"></a>Comentarios

Esto es una clase auxiliar para colorear los mapas de bits semitransparente y no está diseñado para ser llamado directamente por el programador.

Cuando se usa la versión del método que tiene *dstPixel*, el color final es una combinación de *dstPixel* y *srcPixel*. El *srcPixel* color es el color parcialmente transparente sobre el color base *dstPixel*.

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

Crea un mapa de bits que se puede usar como una sombra.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parámetros

*nDepth*<br/>
[in] El ancho y alto de la sombra.

*clrBase*<br/>
[in] El color de la sombra.

*iMinBrightness*<br/>
[in] El brillo mínimo de la sombra.

*iMaxBrightness*<br/>
[in] El brillo máximo de la sombra.

### <a name="return-value"></a>Valor devuelto

Un identificador para el mapa de bits creado si este método se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Si *nDepth* se establece en 0, este método se cierra y devuelve NULL. Si *nDepth* sea inferior a 3, el ancho y alto de la sombra se establecen en 3 píxeles.

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

Convierte un color de una representación de color rojo, verde y azul (RGB) a un matiz, saturación y representación de luminosidad (HSL).

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
|Parámetro|Descripción|
|*rgb*|[in] El color de los valores RGB.|
|*H*|[out] Un puntero a un valor doble que el método almacena el matiz del color.|
|*S*|[out] Un puntero a un valor doble que el método almacena la saturación del color.|
|*L*|[out] Un puntero a un valor doble que el método almacena la luminosidad del color.|

### <a name="remarks"></a>Comentarios

Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](/windows/desktop/uxguide/vis-color).

El valor devuelto para *H* se representa como una fracción de entre 0 y 1, donde 0 y 1 representan rojo. Los valores devueltos para *S* y *L* son números comprendidos entre 0 y 1.

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
[in] Color que se va a convertir en una representación RGB.

*H*<br/>
[out] Un puntero a un valor double donde este método almacena el matiz del color resultante.

*S*<br/>
[out] Un puntero a un valor double donde este método almacena la saturación del color resultante.

*V*<br/>
[out] Un puntero a un valor double donde este método almacena el valor para el color resultante.

### <a name="remarks"></a>Comentarios

Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](/windows/desktop/uxguide/vis-color).

El valor devuelto para *H* es un número entre 0 y 360, donde 0 y 360 indican rojo. Los valores de la devolución de *S* y *V* son números comprendidos entre 0 y 1.

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

Los colores de un píxel en un mapa de bits transparente.

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
[in] Un puntero a los valores de bits del mapa de bits.

*rect*<br/>
[in] Un área rectangular en la aplicación. El Administrador de dibujo dibuja una sombra debajo y a la derecha de esta área.

*x*<br/>
[in] La coordenada horizontal del píxel en color.

*y*<br/>
[in] La coordenada vertical del píxel en color.

*percent*<br/>
[in] El porcentaje de transparencia.

*iShadowSize*<br/>
[in] El ancho y alto de la sombra.

*clrBase*<br/>
[in] El color de la sombra.

*bIsRight*<br/>
[in] Un parámetro booleano que indica qué píxel en color. Vea la sección Comentarios para obtener más información.

### <a name="remarks"></a>Comentarios

Este método es un método auxiliar que usa el [CDrawingManager::DrawShadow](#drawshadow) método. Se recomienda que llame a si desea dibujar una sombra, `CDrawingManager::DrawShadow` en su lugar.

Si *bIsRight* está establecida en TRUE, se mide el píxel en color *x* píxeles desde el borde derecho de *rect*. Si es FALSE, se mide el píxel en color *x* píxeles desde el borde izquierdo de *rect*.

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

Cambia un solo píxel en un mapa de bits en el color especificado.

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
|Parámetro|Descripción|
|*pBits*|[in] Un puntero a los valores de bits del mapa de bits.|
|*cx*|[in] El ancho total del mapa de bits.|
|*cy*|[in] La altura total del mapa de bits.|
|*x*|[in] La coordenada x del píxel del mapa de bits a cambiar.|
|*y*|[in] Coordenada y del píxel del mapa de bits a cambiar.|
|*color*|[in] El nuevo color del píxel que se identifica mediante las coordenadas proporcionadas.|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

Combina dos colores según una proporción ponderada.

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
|Parámetro|Descripción|
|*color1*|[in] El primer color mezclar.|
|*color2*|[in] El segundo color mezclar.|
|*dblLumRatio*|[in] La proporción de luminosidad del color nuevo. `SmartMixColors` Multiplica la luminosidad del color mixto en esta proporción antes de determinar el color final.|
|*k1*|[in] La proporción ponderada para el primer color.|
|*k2*|[in] La proporción ponderada del segundo color.|

### <a name="return-value"></a>Valor devuelto

Un color que representa una combinación ponderada de los colores proporcionados.

### <a name="remarks"></a>Comentarios

Este método produce un error si *k1* o *k2* es menor que cero. Si ambos parámetros se establecen en 0, el método devuelve `RGB(0, 0, 0)`.

Se calcula la proporción ponderada con la siguiente fórmula: (color1 \* k1 + color2 \* k2) /(k1 + k2). Después de determina la proporción ponderada, el método calcula la luminosidad del color mixto. A continuación, multiplica la luminosidad por *dblLumRatio*. Si el valor es mayor que 1,0, el método establece la luminosidad del color mixto en el nuevo valor. En caso contrario, se establece la luminosidad a 1.0.

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

Un origen de contenido de los DC dentro del rectángulo especificado se gira 90 grados.

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
El contexto de dispositivo de origen.

*bClockWise*<br/>
TRUE indica Girar + 90 º; FALSE indica Girar-90 grados.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
