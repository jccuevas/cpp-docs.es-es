---
title: Clase CDrawingManager | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9a0255bae48ad61f140bdc8aa8a6091cf10bc77
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdrawingmanager-class"></a>Clase CDrawingManager
La `CDrawingManager` clase implementa algoritmos de dibujo complejos.  
  
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
|[CDrawingManager::DrawAlpha](#drawalpha)|Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.|  
|[CDrawingManager::DrawRotated](#drawrotated)|Gira un origen de contenido de controlador de dominio dentro del rectángulo especificado por +/-90 grados|  
|[CDrawingManager::DrawEllipse](#drawellipse)|Dibuja una elipse con los colores de relleno y borde proporcionados.|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Dibuja un anillo y se rellena con un degradado de color.|  
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
|[CDrawingManager::HuetoRGB](#huetorgb)|Método auxiliar que convierte un valor de matiz en un componente de rojo, verde o azul.|  
|[CDrawingManager::MirrorRect](#mirrorrect)|Voltea un área rectangular.|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|Método auxiliar que determina el color final de un píxel semitransparente.|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Crea un mapa de bits que puede utilizarse como una sombra.|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convierte un color de una representación RGB en una representación HSL.|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convierte un color de una representación RGB en una representación HSV.|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Método auxiliar que los colores de un píxel parcialmente transparente en un mapa de bits.|  
|[CDrawingManager::SetPixel](#setpixel)|Método auxiliar que cambia un solo píxel en un mapa de bits para el color especificado.|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combina dos colores en función de una proporción ponderada.|  
  
## <a name="remarks"></a>Comentarios  
 La `CDrawingManager` clase proporciona funciones para dibujar sombras, degradados de color y rectángulos resaltados. También realiza la combinación alfa. Puede utilizar esta clase para cambiar directamente la interfaz de usuario de la aplicación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdrawmanager.h  
  
##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager  
 Construye un [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) objeto.  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dc`  
 Una referencia a un contexto de dispositivo. El `CDrawingManager` este contexto se utiliza para dibujar.  
  
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
|[in] `size`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) parámetro que indica el tamaño del mapa de bits.|  
|[out] `pBits`|Un puntero a un puntero a datos que recibe la ubicación de la imagen de DIB valores de bit.|  
|`bitmap`|Un identificador para el mapa de bits original|  
|`clrTransparent`|Un valor RGB especificando un color transparente del mapa de bits original.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el mapa de bits DIB recién creado si este método se realiza correctamente; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre cómo crear un mapa de bits DIB, consulte [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491).  
  
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
 [in] `pDstDC`  
 Un puntero al contexto de dispositivo para el destino.  
  
 [in] `rectDst`  
 El rectángulo de destino.  
  
 [in] `pSrcDC`  
 Un puntero al contexto de dispositivo para el origen.  
  
 [in] `rectSrc`  
 El rectángulo de origen.  
  
### <a name="remarks"></a>Comentarios  
 Este método realiza la combinación alfa para dos mapas de bits. Para obtener más información acerca de la combinación alfa, consulte [AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) del SDK de Windows.  
  
##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse  
 Dibuja una elipse con los colores de relleno y borde proporcionados.  
  
```  
void DrawEllipse(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 El rectángulo delimitador de la elipse.  
  
 [in] `clrFill`  
 El color de que este método se usa para rellenar la elipse.  
  
 [in] `clrLine`  
 El color de este método se utiliza como el borde de la elipse.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve sin dibujar una elipse si uno de los colores se establece en -1. También se devuelve sin dibujar una elipse si ambas dimensiones del rectángulo delimitador es 0.  
  
##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing  
 Dibuja un anillo y se rellena con un degradado de color.  
  
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
 [in] `rect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) parámetro que especifica el límite para el anillo de degradado.  
  
 [in] `colorStart`  
 El primer color del degradado.  
  
 [in] `colorFinish`  
 El último color del degradado.  
  
 [in] `colorBorder`  
 El color del borde.  
  
 [in] `nAngle`  
 Un parámetro que especifica el ángulo inicial de dibujo degradado. Este valor debe estar entre 0 y 360.  
  
 [in] `nWidth`  
 El ancho del borde para el anillo.  
  
 [in] `clrFace`  
 El color del interior del anillo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El rectángulo definido por `rect` deben ser al menos 5 píxeles de ancho y 5 píxeles de alto.  
  
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
|[in] `x1`|Coordenada x donde comienza la línea.|  
|[in] `y1`|Coordenada y donde comienza la línea.|  
|[in] `x2`|Coordenada x donde finaliza la línea.|  
|[in] `y2`|Coordenada y donde finaliza la línea.|  
|[in] `clrLine`|El color de la línea.|  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si `clrLine` es igual a -1.  
  
##  <a name="drawrect"></a>  CDrawingManager::DrawRect  
 Dibuja un rectángulo con el color de relleno y borde proporcionado.  
  
```  
void DrawRect(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Los límites del rectángulo.  
  
 [in] `clrFill`  
 El color de que este método se usa para rellenar el rectángulo.  
  
 [in] `clrLine`  
 El color de este método se usa para el borde del rectángulo.  
  
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
 [in] `rect`  
 Un área rectangular en la aplicación. El Administrador de dibujo, dibujará una sombra debajo de esta área.  
  
 [in] `nDepth`  
 El ancho y alto de la sombra.  
  
 [in] `iMinBrightness`  
 El brillo mínimo de la sombra.  
  
 [in] `iMaxBrightness`  
 El brillo máximo de la sombra.  
  
 [in] `pBmpSaveBottom`  
 Un puntero a un mapa de bits que contiene la imagen de la parte inferior de la sombra.  
  
 [in] `pBmpSaveRight`  
 Un puntero a un mapa de bits que contiene la imagen de la sombra que se dibuja en el lado derecho del rectángulo.  
  
 [in] `clrBase`  
 Color de la sombra.  
  
 [in] `bRightShadow`  
 Un parámetro booleano que indica cómo se dibuja la sombra. Si `bRightShadow` es `TRUE`, `DrawShadow` dibuja una sombra en el lado derecho del rectángulo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Puede proporcionar dos mapas de bits válidas sombras derecho e inferior mediante los parámetros `pBmpSaveBottom` y `pBmpSaveRight`. Si estos [CBitmap](../../mfc/reference/cbitmap-class.md) objetos tienen un objeto GDI adjunto, `DrawShadow` utilizará los mapas de bits como las sombras. Si el `CBitmap` parámetros no tiene un objeto GDI adjunto, `DrawShadow` dibuja la sombra y adjunta los mapas de bits a los parámetros. En futuras llamadas a `DrawShadow`, puede proporcionar estos mapas de bits para acelerar el proceso de dibujo. Para obtener más información sobre la `CBitmap` clase y objetos GDI, vea [objetos gráficos](../../mfc/graphic-objects.md).  
  
 Si alguno de estos parámetros es `NULL`, `DrawShadow` automáticamente, se dibujará la sombra.  
  
 Si establece `bRightShadow` a `FALSE`, se dibujará la sombra debajo y a la izquierda del área rectangular.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `DrawShadow` método de la `CDrawingManager` clase. Este fragmento de código forma parte de la [ejemplo de demostración de la hoja de Prop](../../visual-cpp-samples.md).  
  
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
 [in] `rect`  
 Rectángulo que se va a rellenar.  
  
 [in] `colorStart1`  
 Color inicial del degradado de color de primer.  
  
 [in] `colorFinish1`  
 Color final del degradado de color de primer.  
  
 [in] `colorStart2`  
 Color inicial del degradado de color de segundo.  
  
 [in] `colorFinish2`  
 Color final del degradado de color de segundo.  
  
 [in] `bHorz`  
 Un parámetro booleano que indica si `Fill4ColorsGradient` colores un degradado horizontal o vertical. `TRUE` indica un degradado horizontal.  
  
 [in] `nPercentage`  
 Un entero entre 0 y 100. Este valor indica el porcentaje del rectángulo va a rellenar con el primer degradado de color.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llena un rectángulo con dos degradados de color, se encuentra por encima de ellos o siguiente entre sí, dependiendo del valor de `bHorz`. Cada degradado de color se calcula de forma independiente con el método [CDrawingManager::FillGradient](#fillgradient).  
  
 Este método genera un error de aserción si `nPercentage` es menor que 0 o mayor que 100.  
  
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
 [in] `rect`  
 El área rectangular a rellenar.  
  
 [in] `colorStart`  
 El primer color del degradado.  
  
 [in] `colorFinish`  
 El color final del degradado.  
  
 [in] `bHorz`  
 Un parámetro booleano que especifica si `FillGradient` debe dibujar un degradado horizontal o vertical.  
  
 [in] `nStartFlatPercentage`  
 El porcentaje del rectángulo que `FillGradient` rellena con `colorStart` antes de iniciar el degradado.  
  
 [in] `nEndFlatPercentage`  
 El porcentaje del rectángulo que `FillGradient` rellena con `colorFinish` cuando finaliza el degradado.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `FillGradient` método de la `CDrawingManager` clase. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../visual-cpp-samples.md).  
  
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
 [in] `rect`  
 El área rectangular a rellenar.  
  
 [in] `colorStart`  
 El primer color del degradado.  
  
 [in] `colorFinish`  
 El último color del degradado.  
  
 [in] `nAngle`  
 Un entero entre 0 y 360. Este parámetro especifica la dirección del degradado de color.  
  
### <a name="remarks"></a>Comentarios  
 Use `nAngle` para especificar la dirección del degradado de color. Cuando se especifica la dirección del degradado de color, también especifique donde se inicia el degradado de color. Un valor de 0 para `nAngle` indica que se inicia el gradiente de la parte superior del rectángulo. Como `nAngle` aumenta, la ubicación inicial para el degradado se mueve en una dirección hacia la izquierda según el ángulo.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `FillGradient2` método de la `CDrawingManager` clase. Este fragmento de código forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
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
 [in] `rect`  
 El área rectangular a rellenar.  
  
 [in] `nPercentage`  
 El porcentaje de gris que desee en el rectángulo.  
  
 [in] `clrTransparent`  
 El color transparente.  
  
 [in] `clrDisabled`  
 El color que se utiliza este método para eliminación saturación si `nPercentage` se establece en -1.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el método se realizó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para el parámetro `nPercentage`, un valor inferior indica un color más oscuro.  
  
 El valor máximo de `nPercentage` es 200. Un valor mayor que 200 no cambia la apariencia del rectángulo. Si el valor es -1, este método usa `clrDisabled` para limitar la saturación del rectángulo.  
  
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
 [in] `rect`  
 Un área rectangular para resaltar.  
  
 [in] `nPercentage`  
 Un porcentaje que indica cómo transparente debe ser el resaltado.  
  
 [in] `clrTransparent`  
 El color transparente.  
  
 [in] `nTolerance`  
 Un entero entre 0 y 255 que indica la tolerancia de color.  
  
 [in] `clrBlend`  
 El color base para una combinación.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el método es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si `nPercentage` está comprendido entre 0 y 99, `HighlightRect` utiliza el algoritmo de mezcla de alfa. Para obtener más información acerca de la combinación alfa, consulte [alfa fusión líneas y rellenos](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si `nPercentage` es -1, este método utiliza el nivel de resaltado predeterminado. Si `nPercentage` es 100, este método no hace nada y devuelve `TRUE`.  
  
 El método usa el parámetro `nTolerance` para determinar si quiere resaltar el área rectangular. Para resaltar el rectángulo, la diferencia entre el color de fondo de la aplicación y `clrTransparent` debe ser menor que `nTolerance` en cada componente de color (rojo, verde y azul).  
  
##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE  
 Convierte un color de una representación de HLS en una representación RGB.  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `H`  
 Un número entre 0 y 1 que representa el matiz del color.  
  
 [in] `L`  
 Un número entre 0 y 1 que indica la luminosidad del color.  
  
 [in] `S`  
 Un número comprendido entre 0 y 1 que indica la saturación del color.  
  
### <a name="return-value"></a>Valor devuelto  
 La representación de RGB del color HLS proporcionado.  
  
### <a name="remarks"></a>Comentarios  
 Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Este método y el `CDrawingManager::HLStoRGB_TWO` método realizar la misma operación, pero requieren valores diferentes para el `H` parámetro. En este método, `H` es un porcentaje del círculo. En el `CDrawingManager::HLStoRGB_TWO` método `H` es un valor de grado entre 0 y 360, que representan rojo. Por ejemplo, con `HLStoRGB_ONE`, un valor de 0,25 para `H` es equivalente a un valor de 90 con `HLStoRGB_TWO`.  
  
##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO  
 Convierte un color de una representación de HLS en una representación RGB.  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `H`  
 Un número entre 0 y 360, que representa el matiz del color.  
  
 [in] `L`  
 Un número entre 0 y 1 que indica la luminosidad del color.  
  
 [in] `S`  
 Un número comprendido entre 0 y 1 que indica la saturación del color.  
  
### <a name="return-value"></a>Valor devuelto  
 La representación de RGB del color HLS proporcionado.  
  
### <a name="remarks"></a>Comentarios  
 Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Este método y el [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) método realizar la misma operación, pero requieren valores diferentes para el `H` parámetro. En este método, `H` es un valor de grado entre 0 y 360, que representan rojo. En el [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) método `H` es un porcentaje del círculo. Por ejemplo, con `HLStoRGB_ONE`, un valor de 0,25 para `H` es equivalente a un valor de 90 con `HLStoRGB_TWO`.  
  
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
|[in] `H`|Un número entre 0 y 360, que indica el matiz del color.|  
|[in] `S`|Un número comprendido entre 0 y 1 que indica la saturación del color.|  
|[in] `V`|Un número comprendido entre 0 y 1 que indica el valor para el color.|  
  
### <a name="return-value"></a>Valor devuelto  
 La representación de RGB del color HSV proporcionado.  
  
### <a name="remarks"></a>Comentarios  
 Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB  
 Convierte un valor de matiz en un componente de rojo, verde o azul.  
  
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
 [in] `m1`  
 Vea la sección Comentarios.  
  
 [in] `m2`  
 Vea la sección Comentarios.  
  
 [in] `h`  
 Vea la sección Comentarios.  
  
 [in] `rm1`  
 Vea la sección Comentarios.  
  
 [in] `rm2`  
 Vea la sección Comentarios.  
  
 [in] `rh`  
 Vea la sección Comentarios.  
  
### <a name="return-value"></a>Valor devuelto  
 El componente rojo, verde o azul individual para el matiz proporcionado.  
  
### <a name="remarks"></a>Comentarios  
 Este método es un método auxiliar que la `CDrawingManager` clase utiliza para calcular los componentes individuales de rojos, verde y azules de un color en una representación HSV o HSL. Este método no está diseñado para ser llamado directamente por el programador. Los parámetros de entrada son valores que dependen del algoritmo de conversión.  
  
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
 [in] `rect`  
 El rectángulo delimitador del área que desea voltear.  
  
 [in] `bHorz`  
 Un parámetro booleano que indica si el rectángulo voltea horizontal o verticalmente.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede desplazarse en cualquier área del contexto de dispositivo propiedad de la `CDrawingManager` clase. Si `bHorz` se establece en `TRUE`, este método voltea el área horizontalmente. En caso contrario, voltea el área verticalmente.  
  
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
 [in] `srcPixel`  
 El color inicial para el píxel.  
  
 [in] `percent`  
 Un número entre 0 y 100 que representa el porcentaje de transparencia. Un valor de 100 indica que el color inicial es completamente transparente.  
  
 [in] `percentR`  
 Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente rojo.  
  
 [in] `percentG`  
 Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente verde.  
  
 [in] `percentB`  
 Un número entre 0 y 100 que representa el porcentaje de transparencia para el componente azul.  
  
 [in] `dstPixel`  
 El color base para el píxel.  
  
### <a name="return-value"></a>Valor devuelto  
 El color final del píxel semitransparente.  
  
### <a name="remarks"></a>Comentarios  
 Esto es una clase auxiliar para colorear los mapas de bits semitransparentes y no está diseñado para ser llamado directamente por el programador.  
  
 Cuando se utiliza la versión del método que tiene `dstPixel`, el color final es una combinación de `dstPixel` y `srcPixel`. El `srcPixel` color es el color transparente parcial sobre el color base de `dstPixel`.  
  
##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask  
 Crea un mapa de bits que puede utilizarse como una sombra.  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nDepth`  
 El ancho y alto de la sombra.  
  
 [in] `clrBase`  
 Color de la sombra.  
  
 [in] `iMinBrightness`  
 El brillo mínimo de la sombra.  
  
 [in] `iMaxBrightness`  
 El brillo máximo de la sombra.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el mapa de bits creado si este método se realiza correctamente; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Si `nDepth` se establece en 0, este método se cierra y devuelve `NULL`. Si `nDepth` es inferior a 3, el ancho y alto de la sombra se establecen en 3 píxeles.  
  
##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL  
 Convierte un color de una representación de rojo, verde y azul (RGB) a un matiz, saturación y representación de luminosidad (HSL).  
  
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
|[in] `rgb`|El color de los valores RGB.|  
|[out] `H`|Un puntero a un tipo double donde el método almacena el matiz del color.|  
|[out] `S`|Un puntero a un tipo double donde el método almacena la saturación del color.|  
|[out] `L`|Un puntero a un tipo double donde el método almacena la luminosidad del color.|  
  
### <a name="remarks"></a>Comentarios  
 Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 El valor devuelto para `H` se representa como una fracción de entre 0 y 1, donde 0 y 1 representan rojo. Los valores devueltos para `S` y `L` son números entre 0 y 1.  
  
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
 [in] `rgb`  
 El color que desea convertir en una representación RGB.  
  
 [out] `H`  
 Un puntero a un tipo double donde este método almacena el matiz del color resultante.  
  
 [out] `S`  
 Un puntero a un tipo double donde este método almacena la saturación del color resultante.  
  
 [out] `V`  
 Un puntero a un tipo double donde este método almacena el valor para el color resultante.  
  
### <a name="remarks"></a>Comentarios  
 Un color puede representarse como HSV (matiz, saturación y valor), HSL (matiz, saturación y luminosidad) o RGB (rojo, verde y azul). Para obtener más información acerca de las diferentes representaciones del color, vea [Color](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 El valor devuelto de `H` es un número entre 0 y 360, donde 0 y 360, indicar rojo. La devolución de valores de `S` y `V` son números entre 0 y 1.  
  
##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel  
 Los colores de un píxel transparente en un mapa de bits.  
  
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
 [in] `pBits`  
 Un puntero a los valores de bits del mapa de bits.  
  
 [in] `rect`  
 Un área rectangular en la aplicación. El Administrador de dibujo dibuja una sombra debajo y a la derecha de esta área.  
  
 [in] `x`  
 La coordenada horizontal del píxel en color.  
  
 [in] `y`  
 Coordenada vertical del píxel en color.  
  
 [in] `percent`  
 El porcentaje de transparencia.  
  
 [in] `iShadowSize`  
 El ancho y alto de la sombra.  
  
 [in] `clrBase`  
 Color de la sombra.  
  
 [in] `bIsRight`  
 Un parámetro booleano que indica qué píxel en color. Vea la sección Comentarios para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 Este método es un método auxiliar que se usa por la [CDrawingManager::DrawShadow](#drawshadow) método. Se recomienda que si va a dibujar una sombra, llame a `CDrawingManager::DrawShadow` en su lugar.  
  
 Si `bIsRight` está establecido en `TRUE`, se mide el píxel en color `x` píxeles desde el borde derecho de `rect`. Si es `FALSE`, se mide el píxel en color `x` píxeles desde el borde izquierdo del `rect`.  
  
##  <a name="setpixel"></a>  CDrawingManager::SetPixel  
 Cambia un solo píxel en un mapa de bits para el color especificado.  
  
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
|[in] `pBits`|Un puntero a los valores de bits del mapa de bits.|  
|[in] `cx`|El ancho total del mapa de bits.|  
|[in] `cy`|El alto total del mapa de bits.|  
|[in] `x`|La coordenada x del píxel en el mapa de bits a cambiar.|  
|[in] `y`|Coordenada y del píxel en el mapa de bits a cambiar.|  
|[in] `color`|El nuevo color para el píxel que se identifica mediante las coordenadas proporcionadas.|  
  
##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors  
 Combina dos colores en función de una proporción ponderada.  
  
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
|[in] `color1`|El primer color mezclar.|  
|[in] `color2`|El segundo color mezclar.|  
|[in] `dblLumRatio`|La proporción de luminosidad del color nuevo. `SmartMixColors` Multiplica la luminosidad del color mixto en esta relación antes de determinar un color final.|  
|[in] `k1`|La proporción ponderada para el primer color.|  
|[in] `k2`|La proporción ponderada del segundo color.|  
  
### <a name="return-value"></a>Valor devuelto  
 Color que representa una combinación de los colores proporcionados ponderada.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si el valor `k1` o `k2` es menor que cero. Si ambos parámetros se establecen en 0, el método devuelve `RGB(0, 0, 0)`.  
  
 Se calcula la proporción ponderada con la siguiente fórmula: (color1 * k1 + color2 \* k2) /(k1 + k2). Una vez determinada la proporción ponderada, el método calcula la luminosidad del color mixto. A continuación, multiplica la luminosidad por `dblLumRatio`. Si el valor es mayor que 1.0, el método establece la luminosidad del color mixto en el nuevo valor. En caso contrario, se establece la luminosidad a 1.0.  
  
##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated  
 Un origen de contenido de controlador de dominio dentro del rectángulo especificado se gira 90 grados.  
  
```  
void DrawRotated(
    CRect rectDest,  
    CDC& dcSrc,  
    BOOL bClockWise);
```  
  
### <a name="parameters"></a>Parámetros  
 `rectDest`  
 Rectángulo de destino.  
  
 `dcSrc`  
 El contexto de dispositivo de origen.  
  
 `bClockWise`  
 `TRUE` indica el giro + 90 º; `FALSE` indica giro-90 grados.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
