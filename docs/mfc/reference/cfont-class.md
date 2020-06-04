---
title: Clase CFont
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: 36fd469b182d5f3e0d3449112d04c1a8623d7526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373841"
---
# <a name="cfont-class"></a>Clase CFont

Encapsula una fuente de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular la fuente.

## <a name="syntax"></a>Sintaxis

```
class CFont : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFont::CFont](#cfont)|Construye un objeto `CFont`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Inicializa a `CFont` con las características especificadas.|
|[CFont::CreateFontIndirect](#createfontindirect)|Inicializa un `CFont` objeto con las `LOGFONT` características dadas en una estructura.|
|[CFont::CreatePointFont](#createpointfont)|Inicializa a `CFont` con la altura especificada, medida en décimas de punto y tipo de letra.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Igual `CreateFontIndirect` que excepto que la altura de la fuente se mide en décimas de punto en lugar de unidades lógicas.|
|[CFont::FromHandle](#fromhandle)|Devuelve un puntero `CFont` a un objeto cuando se le da un HFONT de Windows.|
|[CFont::GetLogFont](#getlogfont)|Rellena una `LOGFONT` con información sobre la `CFont` fuente lógica adjunta al objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFont::operador HFONT](#operator_hfont)|Devuelve el identificador de fuente `CFont` GDI de Windows asociado al objeto.|

## <a name="remarks"></a>Observaciones

Para utilizar `CFont` un objeto, construya un `CFont` objeto y adjúntelo una fuente de Windows con [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont)o [CreatePointFontIndirect](#createpointfontindirect)y, a continuación, utilice las funciones miembro del objeto para manipular la fuente.

Las `CreatePointFont` `CreatePointFontIndirect` funciones y a `CreateFont` menudo `CreateFontIndirect` son más fáciles de usar que o ya que realizan automáticamente la conversión para la altura de la fuente de un tamaño de punto a unidades lógicas.

Para obtener `CFont`más información sobre , consulte [Objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a>CFont::CFont

Construye un objeto `CFont`.

```
CFont();
```

### <a name="remarks"></a>Observaciones

El objeto resultante debe `CreateFont`inicializarse `CreatePointFont`con `CreatePointFontIndirect` , `CreateFontIndirect`, , o antes de que se pueda utilizar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a>CFont::CreateFont

Inicializa un `CFont` objeto con las características especificadas.

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>Parámetros

*nAltura*<br/>
Especifica la altura deseada (en unidades lógicas) de la fuente. Consulte `lfHeight` el miembro de la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)en el Windows SDK para obtener una descripción. El valor absoluto de *nHeight* no debe superar las 16.384 unidades de dispositivo después de convertirlo. Para todas las comparaciones de altura, el asignador de fuentes busca la fuente más grande que no supere el tamaño solicitado o la fuente más pequeña si todas las fuentes superan el tamaño solicitado.

*nAncho*<br/>
Especifica el ancho medio (en unidades lógicas) de los caracteres de la fuente. Si *nWidth* es 0, la relación de aspecto del dispositivo se hará coincidir con la relación de aspecto de digitalización de las fuentes disponibles para encontrar la coincidencia más cercana, que viene determinada por el valor absoluto de la diferencia.

*nEscapement*<br/>
Especifica el ángulo (en unidades de 0,1 grados) entre el vector de escape y el eje X de la superficie de visualización. El vector de escape es la línea a través de los orígenes del primer y último carácter de una línea. El ángulo se mide en sentido antihorario desde el eje X. Consulte `lfEscapement` el miembro `LOGFONT` de la estructura en el Windows SDK para obtener más información.

*nOrientación*<br/>
Especifica el ángulo (en unidades de 0,1 grados) entre la línea base de un carácter y el eje X. El ángulo se mide en sentido antihorario desde el eje X para los sistemas de coordenadas en los que la dirección Y está hacia abajo y en el sentido de las agujas del reloj desde el eje X para los sistemas de coordenadas en los que la dirección Y está hacia arriba.

*nPeso*<br/>
Especifica el peso de fuente (en píxeles con tinta por 1000). Consulte el miembro *lfWeight* en la `LOGFONT` estructura del Windows SDK para obtener más información. Los valores descritos son aproximados; la apariencia real depende del tipo de letra. Algunas fuentes solo tienen pesos FW_NORMAL, FW_REGULAR y FW_BOLD. Si se especifica FW_DONTCARE, se utiliza un peso predeterminado.

*bItalic*<br/>
Especifica si la fuente está en cursiva.

*bSubrayado*<br/>
Especifica si la fuente está subrayada.

*cStrikeOut*<br/>
Especifica si los caracteres de la fuente se desmayan. Especifica una fuente de tachado si se establece en un valor distinto de cero.

*nCharSet*<br/>
Especifica el juego de caracteres `lfCharSet` de `LOGFONT` la fuenteVer el miembro en la estructura en el Windows SDK para obtener una lista de valores.

El juego de caracteres OEM depende del sistema.

Las fuentes con otros conjuntos de caracteres pueden existir en el sistema. Una aplicación que utiliza una fuente con un juego de caracteres desconocido no debe intentar traducir o interpretar cadenas que se van a representar con esa fuente. En su lugar, las cadenas deben pasarse directamente al controlador del dispositivo de salida.

El asignador de fuentes no utiliza el valor DEFAULT_CHARSET. Una aplicación puede utilizar este valor para permitir que el nombre y el tamaño de una fuente describan completamente la fuente lógica. Si no existe una fuente con el nombre especificado, se puede sustituir una fuente de cualquier juego de caracteres por la fuente especificada. Para evitar resultados inesperados, las aplicaciones deben usar el valor DEFAULT_CHARSET con moderación.

*nOutPrecision*<br/>
Especifica la precisión de salida deseada. La precisión de salida define la precisión de salida que debe coincidir con la altura, el ancho, la orientación del carácter, el escape y el tono de la fuente solicitada. Consulte `lfOutPrecision` el miembro `LOGFONT` de la estructura en el Windows SDK para obtener una lista de valores y más información.

*nClipPrecision*<br/>
Especifica la precisión de recorte deseada. La precisión de recorte define cómo recortar caracteres que están parcialmente fuera de la región de recorte. Consulte `lfClipPrecision` el miembro `LOGFONT` de la estructura en el Windows SDK para obtener una lista de valores.

Para utilizar una fuente incrustada de solo lectura, una aplicación debe especificar CLIP_ENCAPSULATE.

Para lograr una rotación coherente de dispositivos, TrueType y fuentes vectoriales, una aplicación puede usar el operador OR para combinar el valor CLIP_LH_ANGLES con cualquiera de los otros valores *nClipPrecision.* Si se establece el bit CLIP_LH_ANGLES, la rotación de todas las fuentes depende de si la orientación del sistema de coordenadas es zurda o diestra. (Para obtener más información sobre la orientación de los sistemas de coordenadas, consulte la descripción del parámetro *nOrientation.)* Si no se establece CLIP_LH_ANGLES, las fuentes del dispositivo siempre giran en sentido contrario a las agujas del reloj, pero la rotación de otras fuentes depende de la orientación del sistema de coordenadas.

*nCalidad*<br/>
Especifica la calidad de salida de la fuente, que define la cuidadosa relación con la que la GDI debe intentar hacer coincidir los atributos de fuente lógica con los de una fuente física real. Consulte `lfQuality` el miembro `LOGFONT` de la estructura en el Windows SDK para obtener una lista de valores.

*nPitchAndFamily*<br/>
Especifica el paso y la familia de la fuente. Consulte `lfPitchAndFamily` el miembro `LOGFONT` de la estructura en el Windows SDK para obtener una lista de valores y más información.

*lpszFacename*<br/>
A `CString` o puntero a una cadena terminada en null que especifica el nombre de tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. La función [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) de Windows se puede utilizar para enumerar todas las fuentes disponibles actualmente. Si *lpszFacename* es NULL, el GDI utiliza un tipo de letra independiente del dispositivo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La fuente se puede seleccionar posteriormente como fuente para cualquier contexto de dispositivo.

La `CreateFont` función no crea una nueva fuente GDI de Windows. Simplemente selecciona la coincidencia más cercana de las fuentes físicas disponibles para el GDI.

Las aplicaciones pueden utilizar la configuración predeterminada para la mayoría de los parámetros al crear una fuente lógica. Los parámetros que siempre se deben asignar valores específicos son *nHeight* y *lpszFacename*. Si la aplicación no establece *nHeight* y *lpszFacename,* la fuente lógica que se crea depende del dispositivo.

Cuando termine con `CFont` el objeto `CreateFont` creado `CDC::SelectObject` por la función, utilice para seleccionar `CFont` una fuente diferente en el contexto del dispositivo y, a continuación, elimine el objeto que ya no es necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a>CFont::CreateFontIndirect

Inicializa un `CFont` objeto con las características proporcionadas en una estructura [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
Apunta a `LOGFONT` una estructura que define las características de la fuente lógica.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La fuente se puede seleccionar posteriormente como la fuente actual para cualquier dispositivo.

Esta fuente tiene las características especificadas en la estructura [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw) Cuando se selecciona la fuente mediante la función miembro [CDC::SelectObject,](../../mfc/reference/cdc-class.md#selectobject) el asignador de fuentes GDI intenta hacer coincidir la fuente lógica con una fuente física existente. Si el asignador de fuentes no encuentra una coincidencia exacta para la fuente lógica, proporciona una fuente alternativa cuyas características coinciden con tantas características solicitadas como sea posible.

Cuando ya no `CFont` necesite el `CreateFontIndirect` objeto `CDC::SelectObject` creado por la función, utilice para `CFont` seleccionar una fuente diferente en el contexto del dispositivo y, a continuación, elimine el objeto que ya no es necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a>CFont::CreatePointFont

Esta función proporciona una forma sencilla de crear una fuente de un tipo de letra y un tamaño de punto especificados.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parámetros

*nPointSize*<br/>
Altura de fuente solicitada en décimas de punto. (Por ejemplo, pase 120 para solicitar una fuente de 12 puntos.)

*lpszFaceName*<br/>
A `CString` o puntero a una cadena terminada en null que especifica el nombre de tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. La función 'EnumFontFamilies de Windows se puede utilizar para enumerar todas las fuentes disponibles actualmente. Si *lpszFaceName* es NULL, el GDI utiliza un tipo de letra independiente del dispositivo.

*pDC*<br/>
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) que se usará para convertir el alto en *nPointSize* en unidades lógicas. Si ES NULL, se usa un contexto de dispositivo de pantalla para la conversión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Convierte automáticamente el alto en *nPointSize* en unidades lógicas mediante el objeto CDC al que apunta *pDC*.

Cuando termine con `CFont` el objeto `CreatePointFont` creado por la función, seleccione primero `CFont` la fuente fuera del contexto del dispositivo y, a continuación, elimine el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect

Esta función es la misma que [CreateFontIndirect](#createfontindirect) excepto que el `lfHeight` miembro de la `LOGFONT` se interpreta en décimas de punto en lugar de unidades de dispositivo.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
Apunta a una estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) que define las características de la fuente lógica. El `lfHeight` miembro `LOGFONT` de la estructura se mide en décimas de punto en lugar de unidades lógicas. (Por ejemplo, `lfHeight` establezca en 120 para solicitar una fuente de 12 puntos.)

*pDC*<br/>
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) que se utilizará `lfHeight` para convertir la altura en unidades lógicas. Si ES NULL, se usa un contexto de dispositivo de pantalla para la conversión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función convierte automáticamente `lfHeight` la altura en unidades lógicas mediante `LOGFONT` el objeto CDC al que apunta *pDC* antes de pasar la estructura a Windows.

Cuando termine con `CFont` el objeto `CreatePointFontIndirect` creado por la función, seleccione primero `CFont` la fuente fuera del contexto del dispositivo y, a continuación, elimine el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a>CFont::FromHandle

Devuelve un puntero `CFont` a un objeto cuando se le da un identificador HFONT a un objeto de fuente GDI de Windows.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parámetros

*hFont*<br/>
Identificador HFONT de una fuente de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero `CFont` a un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si `CFont` un objeto aún no está asociado `CFont` al identificador, se crea y adjunta un objeto temporal. Este `CFont` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal sólo es válido durante el procesamiento de un mensaje de ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a>CFont::GetLogFont

Llame a esta función `LOGFONT` para `CFont`recuperar una copia de la estructura para .

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parámetros

*pLogFont*<br/>
Puntero a la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) para recibir la información de fuente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente, de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont::operador HFONT

Utilice este operador para obtener el identificador GDI `CFont` de Windows de la fuente adjunta al objeto.

```
operator HFONT() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del objeto de fuente `CFont` GDI de Windows asociado si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Puesto que este operador se `CFont` utiliza automáticamente para las `CFont` conversiones de fuentes y [texto](/windows/win32/gdi/fonts-and-text), puede pasar objetos a funciones que esperan HIFON.

Para obtener más información sobre el uso de objetos gráficos, vea [Objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
