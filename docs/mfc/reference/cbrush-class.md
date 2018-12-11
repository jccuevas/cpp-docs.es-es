---
title: CBrush (clase)
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: dbc5e36fdf613f1db2818ac6193709829e3bd001
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178712"
---
# <a name="cbrush-class"></a>CBrush (clase)

Encapsula un pincel de la Interfaz de dispositivo gráfico (GDI) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Construye un objeto `CBrush`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicializa un pincel con el estilo, el color y el patrón especificado en un [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) estructura.|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicializa un pincel con un patrón especificado por un mapa de bits independientes del dispositivo (DIB).|
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicializa un pincel con el patrón de sombreado especificado y el color.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicializa un pincel con un patrón especificado por un mapa de bits.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicializa un pincel con el color sólido especificado.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Crea un pincel de color predeterminado del sistema.|
|[CBrush::FromHandle](#fromhandle)|Devuelve un puntero a un `CBrush` objeto cuando se especifica un identificador a un Windows `HBRUSH` objeto.|
|[CBrush::GetLogBrush](#getlogbrush)|Obtiene un [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) estructura.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CBrush::operator HBRUSH](#operator_hbrush)|Devuelve el identificador de Windows asociado a la `CBrush` objeto.|

## <a name="remarks"></a>Comentarios

Para usar un `CBrush` objeto, construya un `CBrush` objeto y pasarlo a cualquier `CDC` función miembro que requiere un pincel.

Pinceles pueden ser sólidos, generan o entramado.

Para obtener más información sobre `CBrush`, consulte [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cbrush"></a>  CBrush::CBrush

Construye un objeto `CBrush`.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parámetros

*crColor*<br/>
Especifica el color de primer plano del pincel como un color RGB. Si el pincel se generan, este parámetro especifica el color de la sombreado.

*nIndex*<br/>
Especifica el estilo de sombreado del pincel. Puede ser cualquiera de los siguientes valores:

- Sombreado HS_BDIAGONAL hacia abajo (de izquierda a derecha) a 45 grados

- HS_CROSS Horizontal y vertical rayado

- HS_DIAGCROSS Sombreado doble de 45 grados

- HS_FDIAGONAL hacia arriba sombreado (de izquierda a derecha) a 45 grados

- Sombreado HS_HORIZONTAL Horizontal

- Sombreado Vertical HS_VERTICAL

*pBitmap*<br/>
Apunta a un `CBitmap` objeto que especifica un mapa de bits que pinta el pincel.

### <a name="remarks"></a>Comentarios

`CBrush` con cuatro constructores sobrecargados. El constructor sin argumentos crea sin inicializar `CBrush` objeto que se debe inicializar antes de poder usarlo.

Si usa el constructor sin argumentos, debe inicializar resultante `CBrush` objeto con [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), o [CreateDIBPatternBrush](#createdibpatternbrush). Si usa uno de los constructores que toma argumentos, a continuación, ninguna otra inicialización es necesaria. Los constructores con argumentos pueden producir una excepción si se producen errores, mientras que el constructor sin argumentos siempre se realizará correctamente.

El constructor con un único [COLORREF](/windows/desktop/gdi/colorref) parámetro construye un pincel sólido con el color especificado. El color especifica un valor RGB y puede crearse con la macro RGB en WINDOWS. H.

El constructor con dos parámetros, crea un pincel de trama. El *nIndex* parámetro especifica el índice de un patrón de sombreado. El *crColor* parámetro especifica el color.

El constructor con un `CBitmap` parámetro construye un pincel de entramado. El parámetro identifica un mapa de bits. Se supone que el mapa de bits se han creado mediante el uso de [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), o [ CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). El tamaño mínimo para un mapa de bits que se usará en una trama de relleno es 8 x 8 píxeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect

Inicializa un pincel con un estilo, el color y el patrón especificado en un [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) estructura.

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parámetros

*lpLogBrush*<br/>
Apunta a un [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) estructura que contiene información sobre el pincel.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.

Un pincel que se creó utilizando un mapa de bits monocromático (plano 1, 1 bit por píxel) se dibuja utilizando los colores de texto y fondo actuales. Con el color de texto actual se dibujará píxeles representados por un bit establecido en 0. Píxeles representados por un bit establecido en 1 se dibujarán con color de fondo actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush

Inicializa un pincel con el patrón especificado por un mapa de bits independientes del dispositivo (DIB).

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>Parámetros

*hPackedDIB*<br/>
Identifica un objeto de memoria global que contiene un mapa de bits empaquetado de independientes del dispositivo (DIB).

*Nuso*<br/>
Especifica si el `bmiColors[]` campos de la [BITMAPINFO](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo) estructura de datos (parte de la "DIB empaquetan") contienen explícita los valores RGB o índices en la paleta lógica realizada actualmente. El parámetro debe ser uno de los valores siguientes:

- La tabla de colores DIB_PAL_COLORS consta de una matriz de índices de 16 bits.

- DIB_RGB_COLORS la tabla de colores contiene los valores RGB literales.

*lpPackedDIB*<br/>
Apunta a un DIB empaquetado que consta de un `BITMAPINFO` estructura seguido inmediatamente por una matriz de bytes que se definen los píxeles del mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar el pincel para cualquier contexto de dispositivo que admita operaciones de trama.

En la forma de que controlar el formato DIB se diferencian las dos versiones:

- En la primera versión, para obtener un identificador para el formato DIB llamar a la Windows `GlobalAlloc` función para asignar un bloque de memoria global y, a continuación, rellene la memoria con el formato DIB empaquetado.

- En la segunda versión, no es necesario llamar a `GlobalAlloc` asignar memoria para el formato DIB empaquetado.

Consta de un DIB empaquetado de un `BITMAPINFO` seguido inmediatamente de la matriz de bytes que define los píxeles del mapa de bits de estructura de datos. Los mapas de bits que se usa como tramas de relleno deben ser de 8 x 8 píxeles. Si el mapa de bits es mayor, Windows crea una trama de relleno con solo los bits correspondientes a las 8 primeras filas y 8 columnas de píxeles en la esquina superior izquierda del mapa de bits.

Cuando una aplicación, selecciona un pincel de patrón DIB dos colores en un contexto de dispositivo monocromático, Windows pasa por alto los colores especificados en el formato DIB y en su lugar mostrará el pincel de modelo mediante los colores de texto y fondo actuales del contexto del dispositivo. Asignada al primer color (en el desplazamiento 0 en la tabla de colores DIB) de la imagen DIB de píxeles se muestran utilizando el color del texto. Píxeles que se asigna al segundo color (en desplazamiento 1 en la tabla de colores) se muestran usando el color de fondo.

Para obtener información sobre el uso de las siguientes funciones de Windows, consulte el SDK de Windows:

- [CreateDIBPatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrush) (esta función se proporciona únicamente por compatibilidad con aplicaciones escritas para versiones de Windows anteriores a la 3.0; utilice el `CreateDIBPatternBrushPt` función.)

- [CreateDIBPatternBrushPt](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrushpt) (esta función debe usarse para las aplicaciones basadas en Win32).

- [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush

Inicializa un pincel con el patrón de sombreado especificado y el color.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el estilo de sombreado del pincel. Puede ser cualquiera de los siguientes valores:

- Sombreado HS_BDIAGONAL hacia abajo (de izquierda a derecha) a 45 grados

- HS_CROSS Horizontal y vertical rayado

- HS_DIAGCROSS Sombreado doble de 45 grados

- HS_FDIAGONAL hacia arriba sombreado (de izquierda a derecha) a 45 grados

- Sombreado HS_HORIZONTAL Horizontal

- Sombreado Vertical HS_VERTICAL

*crColor*<br/>
Especifica el color de primer plano del pincel como un color RGB (el color de la sombreados). Consulte [COLORREF](/windows/desktop/gdi/colorref) en el SDK de Windows para obtener más información.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush

Inicializa un pincel con un patrón especificado por un mapa de bits.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parámetros

*pBitmap*<br/>
Identifica un mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar el pincel para cualquier contexto de dispositivo que admita operaciones de trama. El mapa de bits identificado por *pBitmap* normalmente se inicializa con el [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), o [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) función.

Los mapas de bits que se usa como tramas de relleno deben ser de 8 x 8 píxeles. Si el mapa de bits es mayor, Windows usará solo los bits correspondientes a las 8 primeras filas y columnas de píxeles en la esquina superior izquierda del mapa de bits.

Un pincel de modelo se puede eliminar sin afectar el mapa de bits asociado. Esto significa que el mapa de bits puede usarse para crear cualquier número de pinceles de trama.

Un pincel que se creó utilizando un mapa de bits monocromático (plano de color de 1, 1 bit por píxel) se dibuja utilizando los colores de texto y fondo actuales. Se dibujan los píxeles representados por un bit establecido en 0 con el color de texto actual. Se dibujan los píxeles representados por un bit establecido en 1 con el color de fondo actual.

Para obtener información sobre el uso de [CreatePatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createpatternbrush), un Windows de función, consulte el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush

Inicializa un pincel con un color sólido especificado.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parámetros

*crColor*<br/>
Un [COLORREF](/windows/desktop/gdi/colorref) estructura que especifica el color del pincel. El color especifica un valor RGB y puede crearse con la macro RGB en WINDOWS. H.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.

Cuando una aplicación ha terminado con el pincel creado por `CreateSolidBrush`, seleccionaría el pincel fuera del contexto de dispositivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CBrush::CBrush](#cbrush).

##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush

Inicializa un color de pincel.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica un índice de color. Este valor corresponde al color usado para pintar uno de los elementos de la ventana de 21. Consulte [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) en el SDK de Windows para obtener una lista de valores.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.

Cuando una aplicación ha terminado con el pincel creado por `CreateSysColorBrush`, seleccionaría el pincel fuera del contexto de dispositivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>  CBrush::FromHandle

Devuelve un puntero a un `CBrush` objeto cuando se especifica un identificador a un Windows [HBRUSH](#operator_hbrush) objeto.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parámetros

*hBrush*<br/>
IDENTIFICADOR de un pincel de GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CBrush` objeto si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si un `CBrush` objeto no está asociado al identificador, un archivo temporal `CBrush` objeto creado y conectado. Este temporal `CBrush` objeto es válido solo hasta la próxima vez que la aplicación tiene tiempo de inactividad en su bucle de eventos. En este momento, se eliminan todos los objetos de gráficos temporales. En otras palabras, el objeto temporal es válido solo durante el procesamiento de mensajes de una ventana.

Para obtener más información sobre el uso de objetos gráficos, consulte [gráfico de objetos](/windows/desktop/gdi/graphic-objects) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CBrush::CBrush](#cbrush).

##  <a name="getlogbrush"></a>  CBrush::GetLogBrush

Llame a esta función miembro para recuperar el `LOGBRUSH` estructura.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parámetros

*pLogBrush*<br/>
Apunta a un [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) estructura que contiene información sobre el pincel.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, y *pLogBrush* es un puntero válido, el valor devuelto es el número de bytes almacenados en el búfer.

Si la función se realiza correctamente, y *pLogBrush* es NULL, el valor devuelto es el número de bytes necesario para contener la información de la función se almacenaría en el búfer.

Si se produce un error en la función, el valor devuelto es 0.

### <a name="remarks"></a>Comentarios

El `LOGBRUSH` estructura define el estilo, color y el patrón de un pincel.

Por ejemplo, llamar a `GetLogBrush` para que coincida con el patrón de un mapa de bits o un color determinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>  CBrush::operator HBRUSH

Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CBrush` objeto.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, un identificador para el objeto GDI de Windows representado por la `CBrush` objeto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este es un operador de conversión, que admite el uso directo de un objeto HBRUSH.

Para obtener más información sobre el uso de objetos gráficos, consulte [gráfico de objetos](/windows/desktop/gdi/graphic-objects) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC PROPDLG](../../visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CBitmap (clase)](../../mfc/reference/cbitmap-class.md)<br/>
[CDC (clase)](../../mfc/reference/cdc-class.md)
