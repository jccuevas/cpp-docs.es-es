---
title: CFont (clase)
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
ms.openlocfilehash: 04136b3550675f0e50f905047fee551e27da7069
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182243"
---
# <a name="cfont-class"></a>CFont (clase)

Encapsula una fuente de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular la fuente.

## <a name="syntax"></a>Sintaxis

```
class CFont : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFont::CFont](#cfont)|Construye un objeto `CFont`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Inicializa un `CFont` con las características especificadas.|
|[CFont::CreateFontIndirect](#createfontindirect)|Inicializa un `CFont` objeto con las características de un `LOGFONT` estructura.|
|[CFont::CreatePointFont](#createpointfont)|Inicializa un `CFont` con el alto especificado, medido en décimas de un punto y el tipo de letra.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Igual que `CreateFontIndirect` , salvo que el alto de fuente se mide en décimas de un punto en lugar de unidades lógicas.|
|[CFont::FromHandle](#fromhandle)|Devuelve un puntero a un `CFont` objeto cuando se especifica un HFONT de Windows.|
|[CFont::GetLogFont](#getlogfont)|Rellena un `LOGFONT` con información acerca de la fuente lógica asociada a la `CFont` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CFont::operator HFONT](#operator_hfont)|Devuelve el identificador de fuente de GDI de Windows asociado a la `CFont` objeto.|

## <a name="remarks"></a>Comentarios

Para usar un `CFont` objeto, construya un `CFont` de objetos y adjuntar una fuente de Windows a él con [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), o [CreatePointFontIndirect](#createpointfontindirect)y, a continuación, utilizar las funciones de miembro del objeto para manipular la fuente.

El `CreatePointFont` y `CreatePointFontIndirect` funciones suelen ser más fáciles de usar que `CreateFont` o `CreateFontIndirect` porque realiza la conversión para el alto de la fuente de un tamaño de punto de unidades lógicas automáticamente.

Para obtener más información sobre `CFont`, consulte [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cfont"></a>  CFont::CFont

Construye un objeto `CFont`.

```
CFont();
```

### <a name="remarks"></a>Comentarios

El objeto resultante debe inicializarse con `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, o `CreatePointFontIndirect` antes de poder usarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>  CFont::CreateFont

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

*nHeight*<br/>
Especifica el alto deseado (en unidades lógicas) de la fuente. Consulte la `lfHeight` miembro de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)estructura en el SDK de Windows para obtener una descripción. El valor absoluto de *nHeight* no debe superar los 16 384 unidades de dispositivo después de convertirse. Para las comparaciones de alto, el asignador de fuentes busca la fuente más grande que no supere el tamaño solicitado o la fuente más pequeña si todas las fuentes superan el tamaño solicitado.

*nWidth*<br/>
Especifica el ancho medio (en unidades lógicas) de caracteres de la fuente. Si *nWidth* es 0, la relación de aspecto del dispositivo se comparará con la relación de aspecto de digitalización de las fuentes disponibles para encontrar la coincidencia más cercana, que viene determinada por el valor absoluto de la diferencia.

*nEscapement*<br/>
Especifica el ángulo (en unidades de grados de 0,1) entre el vector de escape y el eje x de la superficie de pantalla. El vector de escape es la línea a través de los orígenes de los caracteres primeros y últimos en una línea. El ángulo se mide en sentido contrario desde el eje x. Consulte la `lfEscapement` miembro en el `LOGFONT` estructura en el SDK de Windows para obtener más información.

*nOrientation*<br/>
Especifica el ángulo (en unidades de grados de 0,1) entre la línea de base de un carácter y el eje x. El ángulo se mide en sentido contrario desde el eje x para los sistemas de coordenadas en el que la dirección del eje y es hacia abajo y de las agujas del reloj desde el eje x para sistemas de coordenadas en el que la dirección y está activo.

*nWeight*<br/>
Especifica el espesor de fuente (en píxeles dibujados por 1000). Consulte la *lfWeight* miembro en el `LOGFONT` estructura en el SDK de Windows para obtener más información. Los valores descritos son aproximados; el aspecto real depende del tipo de letra. Algunas fuentes tienen ponderaciones solo FW_NORMAL FW_REGULAR y FW_BOLD. Si se especifica FW_DONTCARE, se utiliza un peso predeterminado.

*bItalic*<br/>
Especifica si la fuente es cursiva.

*bUnderline*<br/>
Especifica si la fuente está subrayada.

*cStrikeOut*<br/>
Especifica si se tachado caracteres de la fuente. Especifica una fuente de tachado si establece un valor distinto de cero.

*nCharSet*<br/>
Especifica setSee de caracteres de la fuente del `lfCharSet` miembro en el `LOGFONT` estructura en el SDK de Windows para obtener una lista de valores.

El juego de caracteres OEM es dependiente del sistema.

Las fuentes con otros juegos de caracteres pueden existir en el sistema. Una aplicación que utiliza una fuente con un juego de caracteres desconocido no debe intentar traducir o la interpretación de cadenas que se procesará con esa fuente. En su lugar, las cadenas se deben pasar directamente al controlador de dispositivo de salida.

El asignador de fuentes no utiliza el valor DEFAULT_CHARSET. Una aplicación puede utilizar este valor para permitir que el nombre y el tamaño de una fuente para describir completamente la fuente lógica. Si una fuente con el nombre especificado no existe, se puede sustituir una fuente de cualquier juego de caracteres de la fuente especificada. Para evitar resultados inesperados, las aplicaciones deben usar el valor DEFAULT_CHARSET con moderación.

*nOutPrecision*<br/>
Especifica la precisión del resultado deseado. La precisión del resultado define cómo estrechamente la salida debe coincidir con la fuente solicitada alto, ancho, orientación de los caracteres, escape y tono. Consulte la `lfOutPrecision` miembro en el `LOGFONT` estructura en el SDK de Windows para obtener una lista de valores y obtener más información.

*nClipPrecision*<br/>
Especifica la precisión de recorte deseado. La precisión de recorte define cómo recortar caracteres que están parcialmente fuera de la región de recorte. Consulte la `lfClipPrecision` miembro en el `LOGFONT` estructura en el SDK de Windows para obtener una lista de valores.

Para usar una fuente incrustada de sólo lectura, una aplicación debe especificar CLIP_ENCAPSULATE.

Para lograr la rotación coherente de dispositivos, TrueType y las fuentes de vector, una aplicación puede utilizar el operador OR para combinar el valor CLIP_LH_ANGLES con cualquiera de los demás *nClipPrecision* valores. Si se establece el bit CLIP_LH_ANGLES, la rotación de todas las fuentes depende de si la orientación del sistema de coordenadas es zurda o diestro. (Para obtener más información acerca de la orientación de sistemas de coordenadas, vea la descripción de la *nOrientation* parámetro.) Si no se establece CLIP_LH_ANGLES, fuentes de dispositivo siempre Girar a la izquierda, pero la rotación de otras fuentes es dependiente de la orientación del sistema de coordenadas.

*nQuality*<br/>
Especifica la calidad de salida de la fuente, que define cómo cuidadosamente la GDI debe intentar hacer coincidir los atributos de fuente lógica con los de una fuente física real. Consulte la `lfQuality` miembro en el `LOGFONT` estructura en el SDK de Windows para obtener una lista de valores.

*nPitchAndFamily*<br/>
Especifica el cabeceo y la familia de la fuente. Consulte la `lfPitchAndFamily` miembro en el `LOGFONT` estructura en el SDK de Windows para obtener una lista de valores y obtener más información.

*lpszFacename*<br/>
Un `CString` o puntero a una cadena terminada en null que especifica el nombre de tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. El Windows [EnumFontFamilies](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesa) función se puede usar para enumerar todas las fuentes disponibles actualmente. Si *lpszFacename* es NULL, la GDI usa un tipo de letra independientes del dispositivo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar la fuente como la fuente de cualquier contexto de dispositivo.

El `CreateFont` función no crea una nueva fuente de Windows GDI. Simplemente selecciona a la coincidencia más próxima de las fuentes físicas disponibles para la GDI.

Las aplicaciones pueden usar la configuración predeterminada para la mayoría de los parámetros al crear una fuente lógica. Los parámetros que siempre se deben proporcionar valores específicos son *nHeight* y *lpszFacename*. Si *nHeight* y *lpszFacename* no se han establecido por la aplicación, la fuente lógica que se crea depende del dispositivo.

Cuando termine con el `CFont` objeto creado por el `CreateFont` función, utilice `CDC::SelectObject` para seleccionar una fuente diferente en el contexto de dispositivo, a continuación, elimine la `CFont` objeto que ya no es necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>  CFont::CreateFontIndirect

Inicializa un `CFont` objeto con las características de un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)estructura.

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
Apunta a un `LOGFONT` estructura que define las características de la fuente lógica.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar la fuente como la fuente actual para cualquier dispositivo.

Esta fuente tiene las características especificadas en el [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura. Cuando se selecciona la fuente mediante el uso de la [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) función miembro, el asignador de fuentes GDI intenta hacer coincidir la fuente lógica a una fuente física existente. Si se produce un error en el asignador de fuentes buscar a una coincidencia exacta para la fuente lógica, proporciona una fuente alternativo cuyas características coinciden con todas las características solicitadas como sea posible.

Cuando ya no necesita la `CFont` objeto creado por el `CreateFontIndirect` función, utilice `CDC::SelectObject` para seleccionar una fuente diferente en el contexto de dispositivo, a continuación, elimine la `CFont` objeto que ya no es necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>  CFont::CreatePointFont

Esta función proporciona una manera sencilla para crear una fuente de un tipo de letra especificado y el tamaño de punto.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parámetros

*nPointSize*<br/>
Alto de la fuente en décimas de un punto solicitado. (Por ejemplo, pasar 120 para solicitar una fuente de 12 puntos).

*lpszFaceName*<br/>
Un `CString` o puntero a una cadena terminada en null que especifica el nombre de tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. El Windows ' EnumFontFamilies función puede utilizarse para enumerar todas las fuentes disponibles actualmente. Si *lpszFaceName* es NULL, la GDI usa un tipo de letra independientes del dispositivo.

*pDC*<br/>
Puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto que se usará para convertir el alto en *nPointSize* unidades lógicas. Si es NULL, se usa un contexto de dispositivo de pantalla para la conversión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Convierte automáticamente el alto en *nPointSize* unidades lógicas mediante el objeto CDC apunta *pDC*.

Cuando termine con el `CFont` objeto creado por el `CreatePointFont` funcione, primero seleccione la fuente fuera del contexto de dispositivo y luego eliminar el `CFont` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect

Esta función es el mismo que [CreateFontIndirect](#createfontindirect) , salvo que el `lfHeight` miembro de la `LOGFONT` se interpreta en décimas de unidades de un punto en lugar de dispositivo.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
Apunta a un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura que define las características de la fuente lógica. El `lfHeight` miembro de la `LOGFONT` estructura se mide en décimas de un punto en lugar de unidades lógicas. (Por ejemplo, establecer `lfHeight` en 120 para solicitar una fuente de 12 puntos.)

*pDC*<br/>
Puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto que se usará para convertir el alto en `lfHeight` unidades lógicas. Si es NULL, se usa un contexto de dispositivo de pantalla para la conversión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Esta función convierte automáticamente el alto en `lfHeight` unidades lógicas mediante el objeto CDC apunta *pDC* antes de pasar el `LOGFONT` estructura de la sesión en Windows.

Cuando termine con el `CFont` objeto creado por el `CreatePointFontIndirect` funcione, primero seleccione la fuente fuera del contexto de dispositivo y luego eliminar el `CFont` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>  CFont::FromHandle

Devuelve un puntero a un `CFont` objeto cuando se especifica un identificador HFONT a un objeto de fuente de Windows GDI.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parámetros

*hFont*<br/>
Un identificador HFONT una fuente de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CFont` objeto si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si un `CFont` objeto no está asociado al identificador, un archivo temporal `CFont` objeto creado y conectado. Este temporal `CFont` objeto es válido solo hasta que la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, que hora gráfico temporal todos los objetos se eliminan. Otra forma de expresarlo es que el objeto temporal es válido solo durante el procesamiento de mensajes de una ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>  CFont::GetLogFont

Llame a esta función para recuperar una copia de la `LOGFONT` de estructura para `CFont`.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parámetros

*pLogFont*<br/>
Puntero a la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura para recibir la información de fuentes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente, en caso contrario, 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>  CFont::operator HFONT

Utilice este operador para obtener el identificador de GDI de Windows de la fuente que se adjunta a la `CFont` objeto.

```
operator HFONT() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del objeto font GDI de Windows conectados a `CFont` si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Puesto que este operador se usa automáticamente para las conversiones de `CFont` a [fuentes y texto](/windows/desktop/gdi/fonts-and-text), puede pasar `CFont` objetos a funciones que esperan HFONTs.

Para obtener más información sobre el uso de objetos gráficos, consulte [gráfico de objetos](/windows/desktop/gdi/graphic-objects) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
