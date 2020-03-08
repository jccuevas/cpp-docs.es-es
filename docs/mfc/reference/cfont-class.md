---
title: Clase Cfont (
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
ms.openlocfilehash: c37b2f657105e0065e0cddb2c508424bd6c89b0a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866612"
---
# <a name="cfont-class"></a>Clase Cfont (

Encapsula una fuente de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular la fuente.

## <a name="syntax"></a>Sintaxis

```
class CFont : public CGdiObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cfont (:: Cfont (](#cfont)|Construye un objeto `CFont`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cfont (:: CreateFont](#createfont)|Inicializa un `CFont` con las características especificadas.|
|[Cfont (:: CreateFontIndirect](#createfontindirect)|Inicializa un objeto `CFont` con las características proporcionadas en una estructura de `LOGFONT`.|
|[Cfont (:: CreatePointFont](#createpointfont)|Inicializa un `CFont` con el alto especificado, medido en décimas de punto y tipo de letra.|
|[Cfont (:: CreatePointFontIndirect](#createpointfontindirect)|Igual que `CreateFontIndirect`, salvo que el alto de la fuente se mide en décimas de punto en lugar de unidades lógicas.|
|[Cfont (:: FromHandle](#fromhandle)|Devuelve un puntero a un objeto `CFont` cuando se proporciona un HFONT de Windows.|
|[Cfont (:: GetLogFont](#getlogfont)|Rellena un `LOGFONT` con información sobre la fuente lógica asociada al objeto `CFont`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cfont (:: Operator HFONT](#operator_hfont)|Devuelve el identificador de fuente de Windows GDI asociado al objeto de `CFont`.|

## <a name="remarks"></a>Observaciones

Para usar un objeto de `CFont`, construya un objeto `CFont` y adjunte una fuente de Windows con [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont)o [CreatePointFontIndirect](#createpointfontindirect)y, a continuación, use las funciones miembro del objeto para manipular la fuente.

Las funciones `CreatePointFont` y `CreatePointFontIndirect` suelen ser más fáciles de usar que `CreateFont` o `CreateFontIndirect` ya que realizan la conversión para el alto de la fuente a partir de un tamaño de punto a unidades lógicas automáticamente.

Para obtener más información sobre `CFont`, vea [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cfont"></a>Cfont (:: Cfont (

Construye un objeto `CFont`.

```
CFont();
```

### <a name="remarks"></a>Observaciones

El objeto resultante debe inicializarse con `CreateFont`, `CreateFontIndirect`, `CreatePointFont`o `CreatePointFontIndirect` antes de poder usarse.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>Cfont (:: CreateFont

Inicializa un objeto `CFont` con las características especificadas.

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

*nHeight*<br/>
Especifica el alto deseado (en unidades lógicas) de la fuente. Vea el `lfHeight` miembro de la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)en el Windows SDK para obtener una descripción. El valor absoluto de *nHeight* no debe superar las 16.384 unidades de dispositivo una vez convertido. Para todas las comparaciones de alto, el asignador de fuentes busca la fuente más grande que no supere el tamaño solicitado o la fuente más pequeña si todas las fuentes superan el tamaño solicitado.

*nWidth*<br/>
Especifica el ancho medio (en unidades lógicas) de caracteres de la fuente. Si *nWidth* es 0, la relación de aspecto del dispositivo se comparará con la relación de aspecto de digitalización de las fuentes disponibles para encontrar la coincidencia más cercana, que viene determinada por el valor absoluto de la diferencia.

*nEscapement*<br/>
Especifica el ángulo (en unidades de 0,1 grados) entre el vector de escape y el eje x de la superficie de la pantalla. El vector de escape es la línea a través de los orígenes del primer y el último carácter de una línea. El ángulo se mide en sentido contrario a las agujas del reloj desde el eje x. Vea el miembro `lfEscapement` en la estructura `LOGFONT` de la Windows SDK para obtener más información.

*nOrientation*<br/>
Especifica el ángulo (en unidades de 0,1 grados) entre la línea de base de un carácter y el eje x. El ángulo se mide en sentido contrario a las agujas del reloj desde el eje x para los sistemas de coordenadas en los que la dirección y está baja y en el sentido de las agujas del reloj desde el eje x para los sistemas de coordenadas en los que la dirección y está activa.

*nWeight*<br/>
Especifica el espesor de la fuente (en píxeles dibujados por 1000). Para obtener más información, vea el miembro *lfWeight* de la estructura `LOGFONT` en el Windows SDK. Los valores descritos son aproximados; la apariencia real depende del tipo de letra. Algunas fuentes solo tienen FW_NORMAL, FW_REGULAR y pesos FW_BOLD. Si se especifica FW_DONTCARE, se usa una ponderación predeterminada.

*bItalic*<br/>
Especifica si la fuente está en cursiva.

*bUnderline*<br/>
Especifica si la fuente está subrayada.

*cStrikeOut*<br/>
Especifica si se tachan los caracteres de la fuente. Especifica una fuente de tachado si se establece en un valor distinto de cero.

*nCharSet*<br/>
Especifica el conjunto de caracteres de la fuente que se va a `lfCharSet` miembro de la estructura `LOGFONT` de la Windows SDK para obtener una lista de valores.

El juego de caracteres OEM depende del sistema.

Puede haber fuentes con otros juegos de caracteres en el sistema. Una aplicación que utiliza una fuente con un juego de caracteres desconocido no debe intentar traducir ni interpretar cadenas que se van a representar con esa fuente. En su lugar, las cadenas deben pasarse directamente al controlador de dispositivo de salida.

El asignador de fuentes no utiliza el valor DEFAULT_CHARSET. Una aplicación puede utilizar este valor para permitir que el nombre y el tamaño de una fuente describan por completo la fuente lógica. Si no existe una fuente con el nombre especificado, se puede sustituir una fuente de cualquier juego de caracteres por la fuente especificada. Para evitar resultados inesperados, las aplicaciones deben usar el valor DEFAULT_CHARSET con moderación.

*nOutPrecision*<br/>
Especifica la precisión de salida deseada. La precisión de salida define la profundidad con la que la salida debe coincidir con la altura, el ancho, la orientación de caracteres, el escape y el paso de la fuente solicitada. Vea el miembro `lfOutPrecision` en la estructura `LOGFONT` de la Windows SDK para obtener una lista de valores y más información.

*nClipPrecision*<br/>
Especifica la precisión de recorte deseada. La precisión de recorte define cómo se recortan los caracteres que están parcialmente fuera de la región de recorte. Vea el miembro `lfClipPrecision` en la estructura `LOGFONT` de la Windows SDK para obtener una lista de valores.

Para usar una fuente incrustada de solo lectura, una aplicación debe especificar CLIP_ENCAPSULATE.

Para lograr un giro coherente de las fuentes de dispositivo, TrueType y vectoriales, una aplicación puede usar el operador OR para combinar el valor CLIP_LH_ANGLES con cualquiera de los demás valores de *nClipPrecision* . Si se establece el bit de CLIP_LH_ANGLES, el giro de todas las fuentes depende de si la orientación del sistema de coordenadas es zurdo o diestro. (Para obtener más información sobre la orientación de los sistemas de coordenadas, vea la descripción del parámetro *nOrientation* ). Si no se establece CLIP_LH_ANGLES, las fuentes del dispositivo siempre giran en sentido contrario a las agujas del reloj, pero el giro de otras fuentes depende de la orientación del sistema de coordenadas.

*nQuality*<br/>
Especifica la calidad de salida de la fuente, que define la precisión con la que GDI debe intentar hacer coincidir los atributos de fuente lógica con los de una fuente física real. Vea el miembro `lfQuality` en la estructura `LOGFONT` de la Windows SDK para obtener una lista de valores.

*nPitchAndFamily*<br/>
Especifica el paso y la familia de la fuente. Vea el miembro `lfPitchAndFamily` en la estructura `LOGFONT` de la Windows SDK para obtener una lista de valores y más información.

*lpszFacename*<br/>
`CString` o puntero a una cadena terminada en null que especifica el nombre del tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. La función [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) de Windows se puede utilizar para enumerar todas las fuentes disponibles actualmente. Si *lpszFacename* es null, el GDI utiliza un tipo de letra independiente del dispositivo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La fuente se puede seleccionar posteriormente como fuente para cualquier contexto de dispositivo.

La función `CreateFont` no crea una nueva fuente de Windows GDI. Simplemente selecciona la coincidencia más cercana de las fuentes físicas disponibles para la GDI.

Las aplicaciones pueden utilizar la configuración predeterminada para la mayoría de los parámetros al crear una fuente lógica. Los parámetros a los que se les debe asignar siempre valores específicos son *nHeight* y *lpszFacename*. Si la aplicación no establece *nHeight* y *lpszFacename* , la fuente lógica que se crea depende del dispositivo.

Cuando termine con el `CFont` objeto creado por la función `CreateFont`, use `CDC::SelectObject` para seleccionar una fuente diferente en el contexto del dispositivo y, a continuación, elimine el objeto `CFont` que ya no es necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>Cfont (:: CreateFontIndirect

Inicializa un objeto `CFont` con las características proporcionadas en una estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw).

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
Apunta a una estructura de `LOGFONT` que define las características de la fuente lógica.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La fuente se puede seleccionar posteriormente como la fuente actual para cualquier dispositivo.

Esta fuente tiene las características especificadas en la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) . Cuando se selecciona la fuente mediante la función miembro [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) , el asignador de fuentes de GDI intenta hacer coincidir la fuente lógica con una fuente física existente. Si el asignador de fuentes no encuentra una coincidencia exacta para la fuente lógica, proporciona una fuente alternativa cuyas características coinciden con tantas características solicitadas como sea posible.

Cuando ya no necesite el objeto de `CFont` creado por la función `CreateFontIndirect`, use `CDC::SelectObject` para seleccionar una fuente diferente en el contexto del dispositivo y, a continuación, elimine el objeto `CFont` que ya no es necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>Cfont (:: CreatePointFont

Esta función proporciona una manera sencilla de crear una fuente de un tipo de letra y un tamaño de punto especificados.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parámetros

*nPointSize*<br/>
Alto de fuente solicitado en décimas de punto. (Por ejemplo, pase 120 para solicitar una fuente de 12 puntos).

*lpszFaceName*<br/>
`CString` o puntero a una cadena terminada en null que especifica el nombre del tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. La función EnumFontFamilies de Windows se puede utilizar para enumerar todas las fuentes disponibles actualmente. Si *lpszFaceName* es null, el GDI utiliza un tipo de letra independiente del dispositivo.

*pDC*<br/>
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) que se va a utilizar para convertir el alto de *nPointSize* en unidades lógicas. Si es NULL, se usa un contexto de dispositivo de pantalla para la conversión.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Convierte automáticamente el alto de *nPointSize* en unidades lógicas mediante el objeto CDC al que apunta *pDC*.

Cuando termine con el `CFont` objeto creado por la función `CreatePointFont`, seleccione primero la fuente del contexto del dispositivo y, a continuación, elimine el objeto `CFont`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>Cfont (:: CreatePointFontIndirect

Esta función es igual que [CreateFontIndirect](#createfontindirect) , salvo que el miembro `lfHeight` del `LOGFONT` se interpreta en décimas de punto en lugar de unidades de dispositivo.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
Apunta a una estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) que define las características de la fuente lógica. El miembro `lfHeight` de la estructura de `LOGFONT` se mide en décimas de punto en lugar de unidades lógicas. (Por ejemplo, establezca `lfHeight` en 120 para solicitar una fuente de 12 puntos).

*pDC*<br/>
Puntero al objeto [CDC](../../mfc/reference/cdc-class.md) que se va a utilizar para convertir el alto de `lfHeight` en unidades lógicas. Si es NULL, se usa un contexto de dispositivo de pantalla para la conversión.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función convierte automáticamente el alto de `lfHeight` en unidades lógicas usando el objeto CDC al que apunta *pDC* antes de pasar la estructura de `LOGFONT` a Windows.

Cuando termine con el `CFont` objeto creado por la función `CreatePointFontIndirect`, seleccione primero la fuente del contexto del dispositivo y, a continuación, elimine el objeto `CFont`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>Cfont (:: FromHandle

Devuelve un puntero a un objeto `CFont` cuando se proporciona un identificador HFONT a un objeto de fuente de Windows GDI.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parámetros

*hFont*<br/>
Identificador de HFONT de una fuente de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de `CFont` si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Si un objeto de `CFont` no está ya asociado al identificador, se crea y se adjunta un objeto de `CFont` temporal. Este objeto `CFont` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal solo es válido durante el procesamiento de un mensaje de ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>Cfont (:: GetLogFont

Llame a esta función para recuperar una copia de la estructura de `LOGFONT` para `CFont`.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parámetros

*pLogFont*<br/>
Puntero a la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) para recibir la información de la fuente.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se ejecuta correctamente, de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>Cfont (:: Operator HFONT

Utilice este operador para obtener el identificador de GDI de Windows de la fuente asociada al objeto de `CFont`.

```
operator HFONT() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del objeto de fuente de la GDI de Windows asociado a `CFont` si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Puesto que este operador se usa automáticamente para las conversiones de `CFont` a [fuentes y texto](/windows/win32/gdi/fonts-and-text), puede pasar `CFont` objetos a las funciones que esperan HFONTs.

Para obtener más información sobre el uso de objetos gráficos, vea [objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
