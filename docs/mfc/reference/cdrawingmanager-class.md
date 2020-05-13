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
ms.openlocfilehash: 73c5775c2cb83dea79401615b31f2194094fac8e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753239"
---
# <a name="cdrawingmanager-class"></a>Clase CDrawingManager

La `CDrawingManager` clase implementa algoritmos de dibujo complejos.

## <a name="syntax"></a>Sintaxis

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Construye un objeto `CDrawingManager`.|
|`CDrawingManager::~CDrawingManager`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Crea un mapa de bits independiente del dispositivo (DIB) de 32 bits en el que las aplicaciones pueden escribir directamente.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Muestra mapas de bits que tienen píxeles transparentes o semitransparentes.|
|[CDrawingManager::DrawRotated](#drawrotated)|Gira un contenido de DC de origen dentro del rectángulo dado por +/- 90 grados|
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
|[CDrawingManager::MirrorRect](#mirrorrect)|Invierte un área rectangular.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Método auxiliar que determina el color final de un píxel semitransparente.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Crea un mapa de bits que se puede utilizar como sombra.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convierte un color de una representación RGB en una representación HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convierte un color de una representación RGB en una representación HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Método auxiliar que colorea un píxel parcialmente transparente en un mapa de bits.|
|[CDrawingManager::SetPixel](#setpixel)|Método auxiliar que cambia un solo píxel de un mapa de bits al color especificado.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combina dos colores en función de una relación ponderada.|

## <a name="remarks"></a>Observaciones

La `CDrawingManager` clase proporciona funciones para dibujar sombras, degradados de color y rectángulos resaltados. También realiza la mezcla alfa. Puede usar esta clase para cambiar directamente la interfaz de usuario de la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdrawmanager.h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

Construye un [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) objeto.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
[en] Una referencia a un contexto de dispositivo. Utiliza `CDrawingManager` este contexto para dibujar.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

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
|Parámetro|Descripción|
|*size*|[en] Un [CSize](../../atl-mfc-shared/reference/csize-class.md) parámetro que indica el tamaño del mapa de bits.|
|*pBits*|[fuera] Puntero a un puntero de datos que recibe la ubicación de los valores de bits del DIB.|
|*Bits*|Un identificador del mapa de bits original|
|*clrTransparent*|Valor RGB que especifica el color transparente del mapa de bits original.|

### <a name="return-value"></a>Valor devuelto

Un identificador del mapa de bits DIB recién creado si este método se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo crear un mapa de bits DIB, vea [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>CDrawingManager::DrawAlpha

Muestra mapas de bits que tienen píxeles transparentes o semitransparentes.

```cpp
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parámetros

*dDstDC*<br/>
[en] Un puntero al contexto del dispositivo para el destino.

*rectDst*<br/>
[en] El rectángulo de destino.

*pSrcDC*<br/>
[en] Un puntero al contexto del dispositivo para el origen.

*rectSrc*<br/>
[en] El rectángulo de origen.

### <a name="remarks"></a>Observaciones

Este método realiza la combinación alfa para dos mapas de bits. Para obtener más información acerca de la combinación alfa, vea [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) en el Windows SDK.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>CDrawingManager::DrawEllipse

Dibuja una elipse con los colores de relleno y borde proporcionados.

```cpp
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] El rectángulo delimitador de la elipse.

*clrFill*<br/>
[en] El color que utiliza este método para rellenar la elipse.

*clrLine*<br/>
[en] El color que utiliza este método como borde de la elipse.

### <a name="remarks"></a>Observaciones

Este método devuelve sin dibujar una elipse si cualquiera de los colores está establecido en -1. También devuelve sin dibujar una elipse si cualquiera de las dimensiones del rectángulo delimitador es 0.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawingManager::DrawGradientRing

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

*Rect*<br/>
[en] Un [parámetro CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica el límite del anillo de degradado.

*colorStart*<br/>
[en] El primer color para el degradado.

*colorFinish*<br/>
[en] El último color para el degradado.

*colorBorder*<br/>
[en] El color del borde.

*nAngle*<br/>
[en] Parámetro que especifica el ángulo de dibujo de degradado inicial. Este valor debe estar entre 0 y 360.

*nAncho*<br/>
[en] La anchura del borde del anillo.

*clrFace*<br/>
[en] El color del interior del anillo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El rectángulo definido por *rect* debe tener al menos 5 píxeles de ancho y 5 píxeles de alto.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Dibuja una línea.

```cpp
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
|*x1*|[en] Coordenada x donde comienza la línea.|
|*y1*|[en] Coordenada y donde comienza la línea.|
|*x2*|[en] Coordenada x donde termina la línea.|
|*y2*|[en] Coordenada y donde termina la línea.|
|*clrLine*|[en] El color de la línea.|

### <a name="remarks"></a>Observaciones

Se produce un error en este método si *clrLine* es igual a -1.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a>CDrawingManager::DrawRect

Dibuja un rectángulo con los colores de relleno y borde proporcionados.

```cpp
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] Los límites del rectángulo.

*clrFill*<br/>
[en] El color que utiliza este método para rellenar el rectángulo.

*clrLine*<br/>
[en] El color que utiliza este método para el borde del rectángulo.

### <a name="remarks"></a>Observaciones

Este método devuelve sin dibujar un rectángulo si cualquiera de los colores se establece en -1. También devuelve si cualquiera de las dimensiones del rectángulo es 0.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>CDrawingManager::DrawShadow

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

*Rect*<br/>
[en] Un área rectangular en la aplicación. El gestor de dibujos dibujará una sombra debajo de esta área.

*nProfundidad*<br/>
[en] La anchura y la altura de la sombra.

*iMinBrightness*<br/>
[en] El brillo mínimo de la sombra.

*iMaxBrightness*<br/>
[en] El brillo máximo de la sombra.

*pBmpSaveBottom*<br/>
[en] Puntero a un mapa de bits que contiene la imagen de la parte inferior de la sombra.

*pBmpSaveRight*<br/>
[en] Puntero a un mapa de bits que contiene la imagen de la sombra que se dibuja en el lado derecho del rectángulo.

*clrBase*<br/>
[en] El color de la sombra.

*bRightShadow*<br/>
[en] Parámetro booleano que indica cómo se dibuja la sombra. Si *bRightShadow* es `TRUE`, `DrawShadow` dibuja una sombra en el lado derecho del rectángulo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Puede proporcionar dos mapas de bits válidos para las sombras inferior y derecha mediante los parámetros *pBmpSaveBottom* y *pBmpSaveRight*. Si estos [CBitmap](../../mfc/reference/cbitmap-class.md) objetos tienen `DrawShadow` un objeto GDI asociado, usará esos mapas de bits como las sombras. Si `CBitmap` los parámetros no tienen un `DrawShadow` objeto GDI asociado, dibuja la sombra y adjunta los mapas de bits a los parámetros. En futuras `DrawShadow`llamadas a , puede proporcionar estos mapas de bits para acelerar el proceso de dibujo. Para obtener más `CBitmap` información sobre la clase y los objetos GDI, vea [Objetos gráficos](../../mfc/graphic-objects.md).

Si cualquiera de `NULL`estos `DrawShadow` parámetros es , dibujará automáticamente la sombra.

Si establece *bRightShadow* en FALSE, la sombra se dibujará debajo y a la izquierda del área rectangular.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `DrawShadow` muestra `CDrawingManager` cómo utilizar el método de la clase. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de hoja de prop.

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

Rellena un área rectangular con dos degradados de color.

```cpp
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

*Rect*<br/>
[en] El rectángulo que se debe rellenar.

*colorStart1*<br/>
[en] El color inicial para el primer degradado de color.

*colorFinish1*<br/>
[en] El color final para el primer degradado de color.

*colorStart2*<br/>
[en] El color inicial para el segundo degradado de color.

*colorFinish2*<br/>
[en] El color final para el segundo degradado de color.

*bHorz*<br/>
[en] Parámetro booleano que `Fill4ColorsGradient` indica si colorea un degradado horizontal o vertical. TRUE indica un degradado horizontal.

*nPorcentaje*<br/>
[en] Un entero de 0-100. Este valor indica el porcentaje del rectángulo que se va a rellenar con el primer degradado de color.

### <a name="remarks"></a>Observaciones

Cuando un rectángulo se rellena con dos degradados de color, se encuentran uno encima del otro o uno al lado del otro, dependiendo del valor de *bHorz*. Cada degradado de color se calcula de forma independiente con el método [CDrawingManager::FillGradient](#fillgradient).

Este método genera un error de aserción si *nPercentage* es menor que 0 o más de 100.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>CDrawingManager::FillGradient

Rellena un área rectangular con el degradado de color especificado.

```cpp
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] El área rectangular a rellenar.

*colorStart*<br/>
[en] El primer color para el degradado.

*colorFinish*<br/>
[en] El color final para el degradado.

*bHorz*<br/>
[en] Un parámetro booleano `FillGradient` que especifica si se debe dibujar un degradado horizontal o vertical.

*nStartFlatPercentage*<br/>
[en] Porcentaje del rectángulo `FillGradient` que se rellena con *colorStart* antes de iniciar el degradado.

*nEndFlatPercentage*<br/>
[en] El porcentaje del `FillGradient` rectángulo que se rellena con *colorFinalizar* después de que termine el degradado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `FillGradient` muestra `CDrawingManager` cómo utilizar el método de la clase. Este fragmento de código forma parte del ejemplo de demostración de [MS Office 2007.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>CDrawingManager::FillGradient2

Rellena un área rectangular con un degradado de color especificado.

```cpp
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] El área rectangular a rellenar.

*colorStart*<br/>
[en] El primer color del degradado.

*colorFinish*<br/>
[en] El último color del degradado.

*nAngle*<br/>
[en] Un entero entre 0 y 360. Este parámetro especifica la dirección del degradado de color.

### <a name="remarks"></a>Observaciones

Utilice *nAngle* para especificar la dirección del degradado de color. Al especificar la dirección del degradado de color, también se especifica dónde comienza el degradado de color. Un valor de 0 para *nAngle* indica que el degradado comienza desde la parte superior del rectángulo. A medida que aumenta *nAngle,* la ubicación inicial del degradado se mueve en sentido contrario a las agujas del reloj en función del ángulo.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `FillGradient2` muestra `CDrawingManager` cómo utilizar el método de la clase. Este fragmento de código forma parte del [ejemplo New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a>CDrawingManager::GrayRect

Rellena un rectángulo con un color gris especificado.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] El área rectangular a rellenar.

*nPorcentaje*<br/>
[en] El porcentaje de gris que desea en el rectángulo.

*clrTransparent*<br/>
[en] El color transparente.

*clrDisabled*<br/>
[en] El color que este método utiliza para la dessaturación si *nPercentage* se establece en -1.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Para el parámetro *nPercentage*, un valor inferior indica un color más oscuro.

El valor máximo de *nPercentage* es 200. Un valor mayor que 200 no cambia la apariencia del rectángulo. Si el valor es -1, este método utiliza *clrDisabled* para limitar la saturación del rectángulo.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>CDrawingManager::HighlightRect

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

*Rect*<br/>
[en] Un área rectangular para resaltar.

*nPorcentaje*<br/>
[en] Porcentaje que indica cuán transparente debe ser el resaltado.

*clrTransparent*<br/>
[en] El color transparente.

*nTolerancia*<br/>
[en] Un entero entre 0 y 255 que indica la tolerancia de color.

*clrBlend*<br/>
[en] El color base para la fusión.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Si *nPercentage* está entre 0 `HighlightRect` y 99, utiliza el algoritmo de fusión alfa. Para obtener más información sobre la fusión alfa, consulte [Líneas de fusión alfa y rellenos](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si *nPercentage* es -1, este método utiliza el nivel de resaltado predeterminado. Si *nPercentage* es 100, este método no hace nada y devuelve TRUE.

El método utiliza el parámetro *nTolerance* para determinar si se debe resaltar el área rectangular. Para resaltar el rectángulo, la diferencia entre el color de fondo de la aplicación y *clrTransparent* debe ser menor que *nTolerance* en cada componente de color (rojo, verde y azul).

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

Convierte un color de una representación HLS en una representación RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
[en] Un número entre 0 y 1 que representa el matiz del color.

*L*<br/>
[en] Un número entre 0 y 1 que indica la luminosidad del color.

*S*<br/>
[en] Un número entre 0 y 1 que indica la saturación del color.

### <a name="return-value"></a>Valor devuelto

Representación RGB del color HLS proporcionada.

### <a name="remarks"></a>Observaciones

Un color se puede representar como HSV (hue, saturación y valor), HSL (hue, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las diferentes representaciones de color, consulte [Color](/windows/win32/uxguide/vis-color).

Este método `CDrawingManager::HLStoRGB_TWO` y el método realizan la misma operación, pero requieren valores diferentes para el parámetro *H.* En este método, *H* es un porcentaje del círculo. En `CDrawingManager::HLStoRGB_TWO` el método, *H* es un valor de grado entre 0 y 360, que ambos representan rojo. Por ejemplo, `HLStoRGB_ONE`con , un valor de 0,25 para *H* es equivalente a un valor de 90 con `HLStoRGB_TWO`.

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

Convierte un color de una representación HLS en una representación RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
[en] Un número entre 0 y 360 que representa el matiz del color.

*L*<br/>
[en] Un número entre 0 y 1 que indica la luminosidad del color.

*S*<br/>
[en] Un número entre 0 y 1 que indica la saturación del color.

### <a name="return-value"></a>Valor devuelto

Representación RGB del color HLS proporcionada.

### <a name="remarks"></a>Observaciones

Un color se puede representar como HSV (hue, saturación y valor), HSL (hue, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las diferentes representaciones de color, consulte [Color](/windows/win32/uxguide/vis-color).

Este método y el [método CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) realizan la misma operación, pero requieren valores diferentes para el parámetro *H.* En este método, *H* es un valor de grado entre 0 y 360, que ambos representan rojo. En el [método CDrawingManager::HLStoRGB_ONE,](#hlstorgb_one) *H* es un porcentaje del círculo. Por ejemplo, `HLStoRGB_ONE`con , un valor de 0,25 para *H* es equivalente a un valor de 90 con `HLStoRGB_TWO`.

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

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
|*H*|[en] Un número entre 0 y 360 que indica el matiz del color.|
|*S*|[en] Un número entre 0 y 1 que indica la saturación del color.|
|*Ⅴ*|[en] Un número entre 0 y 1 que indica el valor del color.|

### <a name="return-value"></a>Valor devuelto

Representación RGB del color HSV proporcionada.

### <a name="remarks"></a>Observaciones

Un color se puede representar como HSV (hue, saturación y valor), HSL (hue, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las diferentes representaciones de color, consulte [Color](/windows/win32/uxguide/vis-color).

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawingManager::HuetoRGB

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
[en] Consulte Comentarios.

*m2*<br/>
[en] Consulte Comentarios.

*H*<br/>
[en] Consulte Comentarios.

*rm1*<br/>
[en] Consulte Comentarios.

*rm2*<br/>
[en] Consulte Comentarios.

*Rh*<br/>
[en] Consulte Comentarios.

### <a name="return-value"></a>Valor devuelto

El componente rojo, verde o azul individual para el tono proporcionado.

### <a name="remarks"></a>Observaciones

Este método es un `CDrawingManager` método auxiliar que la clase utiliza para calcular los componentes individuales rojo, verde y azul de un color en una representación HSV o HSL. Este método no está diseñado para ser llamado directamente por el programador. Los parámetros de entrada son valores que dependen del algoritmo de conversión.

Para convertir un color HSV o HSL en una representación RGB, llame a uno de los métodos siguientes:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>CDrawingManager::MirrorRect

Invierte un área rectangular.

```cpp
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] El rectángulo delimitador del área que se va a voltear.

*bHorz*<br/>
[en] Un parámetro booleano que indica si el rectángulo se voltea horizontal o verticalmente.

### <a name="remarks"></a>Observaciones

Este método puede voltear cualquier área del `CDrawingManager` contexto del dispositivo propiedad de la clase. Si *bHorz* se establece en TRUE, este método voltea el área horizontalmente. De lo contrario, voltea el área verticalmente.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawingManager::PixelAlpha

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
[en] El color inicial del píxel.

*Por ciento*<br/>
[en] Un número entre 0 y 100 que representa el porcentaje de transparencia. Un valor de 100 indica que el color inicial es completamente transparente.

*percentR*<br/>
[en] Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente rojo.

*percentG*<br/>
[en] Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente verde.

*percentB*<br/>
[en] Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente azul.

*dstPixel*<br/>
[en] El color base del píxel.

### <a name="return-value"></a>Valor devuelto

El color final del píxel semitransparente.

### <a name="remarks"></a>Observaciones

Esta es una clase auxiliar para colorear mapas de bits semitransparentes y no está diseñado para ser llamado directamente por el programador.

Cuando se utiliza la versión del método que tiene *dstPixel*, el color final es una combinación de *dstPixel* y *srcPixel*. El color *srcPixel* es el color parcialmente transparente sobre el color base de *dstPixel*.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask

Crea un mapa de bits que se puede utilizar como sombra.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parámetros

*nProfundidad*<br/>
[en] La anchura y la altura de la sombra.

*clrBase*<br/>
[en] El color de la sombra.

*iMinBrightness*<br/>
[en] El brillo mínimo de la sombra.

*iMaxBrightness*<br/>
[en] El brillo máximo de la sombra.

### <a name="return-value"></a>Valor devuelto

Un identificador del mapa de bits creado si este método se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si *nDepth* se establece en 0, este método se cierra y devuelve NULL. Si *nDepth* es menor que 3, el ancho y el alto de la sombra se establecen en 3 píxeles.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

Convierte un color de una representación roja, verde y azul (RGB) en una representación de matiz, saturación y ligereza (HSL).

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
|*Rgb*|[en] El color en valores RGB.|
|*H*|[fuera] Puntero a un double donde el método almacena el matiz del color.|
|*S*|[fuera] Puntero a un doble donde el método almacena la saturación del color.|
|*L*|[fuera] Puntero a un double donde el método almacena la ligereza del color.|

### <a name="remarks"></a>Observaciones

Un color se puede representar como HSV (hue, saturación y valor), HSL (hue, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las diferentes representaciones de color, consulte [Color](/windows/win32/uxguide/vis-color).

El valor devuelto para *H* se representa como una fracción entre 0 y 1, donde tanto 0 como 1 representan rojo. Los valores devueltos para *S* y *L* son números entre 0 y 1.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

Convierte un color de una representación RGB en una representación HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parámetros

*Rgb*<br/>
[en] El color que se convertirá en una representación RGB.

*H*<br/>
[fuera] Puntero a un double donde este método almacena el matiz resultante para el color.

*S*<br/>
[fuera] Puntero a un double donde este método almacena la saturación resultante para el color.

*Ⅴ*<br/>
[fuera] Puntero a un double donde este método almacena el valor resultante para el color.

### <a name="remarks"></a>Observaciones

Un color se puede representar como HSV (hue, saturación y valor), HSL (hue, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información sobre las diferentes representaciones de color, consulte [Color](/windows/win32/uxguide/vis-color).

El valor devuelto para *H* es un número entre 0 y 360 donde 0 y 360 indican rojo. Los valores devueltos para *S* y *V* son números entre 0 y 1.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

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
[en] Un puntero a los valores de bits para el mapa de bits.

*Rect*<br/>
[en] Un área rectangular en la aplicación. El gestor de dibujos dibuja una sombra debajo y a la derecha de esta área.

*x*<br/>
[en] Coordenada horizontal del píxel a color.

*y y*<br/>
[en] Coordenada vertical del píxel a color.

*Por ciento*<br/>
[en] El porcentaje de transparencia.

*iShadowSize*<br/>
[en] La anchura y la altura de la sombra.

*clrBase*<br/>
[en] El color de la sombra.

*bIsRight*<br/>
[en] Parámetro booleano que indica qué píxel colorear. Para obtener más información, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Este método es un método auxiliar que utiliza el [CDrawingManager::DrawShadow](#drawshadow) método. Se recomienda que si desea dibujar `CDrawingManager::DrawShadow` una sombra, llame en su lugar.

Si *bIsRight* se establece en TRUE, el píxel a color se mide *x* píxeles desde el borde derecho de *rect*. Si es FALSE, el píxel a color se mide *x* píxeles desde el borde izquierdo de *rect*.

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a>CDrawingManager::SetPixel

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
|Parámetro|Descripción|
|*pBits*|[en] Un puntero a los valores de bits del mapa de bits.|
|*Cx*|[en] El ancho total del mapa de bits.|
|*Cy*|[en] La altura total del mapa de bits.|
|*x*|[en] Coordenada x del píxel en el mapa de bits que se ha de cambiar.|
|*y y*|[en] Coordenada y del píxel en el mapa de bits que se ha de cambiar.|
|*Color*|[en] El nuevo color del píxel identificado por las coordenadas proporcionadas.|

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

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
|Parámetro|Descripción|
|*color1*|[en] El primer color que se puede mezclar.|
|*color2*|[en] El segundo color que se puede mezclar.|
|*dblLumRatio*|[en] La relación entre la luminosidad del nuevo color. `SmartMixColors`multiplica la luminosidad del color mezclado por esta proporción antes de determinar un color final.|
|*k1*|[en] La relación ponderada para el primer color.|
|*k2*|[en] La relación ponderada para el segundo color.|

### <a name="return-value"></a>Valor devuelto

Color que representa una mezcla ponderada de los colores suministrados.

### <a name="remarks"></a>Observaciones

Este método produce un error si *k1* o *k2* es menor que cero. Si ambos parámetros se establecen en `RGB(0, 0, 0)`0, el método devuelve .

La relación ponderada se calcula con la \* siguiente fórmula: \* (color1 k1 + color2 k2)/(k1 + k2). Una vez determinada la relación ponderada, el método calcula la luminosidad del color mixto. A continuación, multiplica la luminosidad por *dblLumRatio*. Si el valor es mayor que 1.0, el método establece la luminosidad del color mezclado en el nuevo valor. De lo contrario, la luminosidad se establece en 1.0.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>CDrawingManager::DrawRotated

Gira un contenido de CONTROLADOR de origen dentro del rectángulo dado 90 grados.

```cpp
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parámetros

*rectDest*<br/>
Rectángulo de destino.

*dcSrc*<br/>
El contexto del dispositivo de origen.

*bClockWise*<br/>
TRUE indica rotar +90 grados; FALSE indica rotar -90 grados.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
