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
ms.openlocfilehash: 15132bb5497886638edfe431ae769dd446785df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352478"
---
# <a name="cbrush-class"></a>CBrush (clase)

Encapsula un pincel de la Interfaz de dispositivo gráfico (GDI) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Construye un objeto `CBrush`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicializa un pincel con el estilo, el color y el patrón especificados en una estructura [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicializa un pincel con un patrón especificado por un mapa de bits independiente del dispositivo (DIB).|
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicializa un pincel con el patrón sombreado y el color especificados.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicializa un pincel con un patrón especificado por un mapa de bits.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicializa un pincel con el color sólido especificado.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Crea un pincel que es el color predeterminado del sistema.|
|[CBrush::FromHandle](#fromhandle)|Devuelve un puntero `CBrush` a un objeto cuando `HBRUSH` se le da un identificador a un objeto de Windows.|
|[CBrush::GetLogBrush](#getlogbrush)|Obtiene una estructura [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBrush::operador HBRUSH](#operator_hbrush)|Devuelve el identificador de `CBrush` Windows asociado al objeto.|

## <a name="remarks"></a>Observaciones

Para utilizar `CBrush` un objeto, construya un `CBrush` `CDC` objeto y páselo a cualquier función miembro que requiera un pincel.

Los pinceles pueden ser sólidos, sombreados o estampados.

Para obtener `CBrush`más información sobre , consulte [Objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a>CBrush::CBrush

Construye un objeto `CBrush`.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parámetros

*crColor*<br/>
Especifica el color de primer plano del pincel como un color RGB. Si el pincel está sombreado, este parámetro especifica el color del sombreado.

*nIndex*<br/>
Especifica el estilo de sombreado del pincel. Puede ser cualquiera de los siguientes valores:

- HS_BDIAGONAL escotilla hacia abajo (de izquierda a derecha) a 45 grados

- HS_CROSS rayado horizontal y vertical

- HS_DIAGCROSS Crosshatch a 45 grados

- HS_FDIAGONAL escotilla hacia arriba (de izquierda a derecha) a 45 grados

- HS_HORIZONTAL escotilla horizontal

- HS_VERTICAL escotilla vertical

*pBitmap*<br/>
Apunta a `CBitmap` un objeto que especifica un mapa de bits con el que pinta el pincel.

### <a name="remarks"></a>Observaciones

`CBrush`tiene cuatro constructores sobrecargados. El constructor sin argumentos construye `CBrush` un objeto no inicializado que se debe inicializar antes de que se pueda usar.

Si utiliza el constructor sin argumentos, `CBrush` debe inicializar el objeto resultante con [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)o [CreateDIBPatternBrush](#createdibpatternbrush). Si utiliza uno de los constructores que toma argumentos, no es necesaria ninguna inicialización adicional. Los constructores con argumentos pueden producir una excepción si se encuentran errores, mientras que el constructor sin argumentos siempre se realizará correctamente.

El constructor con un único parámetro [COLORREF](/windows/win32/gdi/colorref) construye un pincel sólido con el color especificado. El color especifica un valor RGB y se puede construir con la macro RGB en WINDOWS. H.

El constructor con dos parámetros construye un pincel de sombreado. El *nIndex* parámetro especifica el índice de un patrón sombreado. El parámetro *crColor* especifica el color.

El constructor `CBitmap` con un parámetro construye un pincel con patrón. El parámetro identifica un mapa de bits. Se supone que el mapa de bits se ha creado mediante [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)o [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). El tamaño mínimo para que un mapa de bits se utilice en un patrón de relleno es de 8 píxeles por 8 píxeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush::CreateBrushIndirect

Inicializa un pincel con un estilo, color y patrón especificados en una estructura [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parámetros

*lpLogBrush*<br/>
Apunta a una estructura [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) que contiene información sobre el pincel.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El pincel se puede seleccionar posteriormente como el pincel actual para cualquier contexto de dispositivo.

Un pincel creado con un mapa de bits monocromo (1 plano, 1 bit por píxel) se dibuja utilizando el texto actual y los colores de fondo. Los píxeles representados por un bit establecido en 0 se dibujarán con el color de texto actual. Los píxeles representados por un bit establecido en 1 se dibujarán con el color de fondo actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush

Inicializa un pincel con el patrón especificado por un mapa de bits independiente del dispositivo (DIB).

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
Identifica un objeto de memoria global que contiene un mapa de bits (DIB) independiente del dispositivo empaquetado.

*nUso*<br/>
Especifica si `bmiColors[]` los campos de la estructura de datos [BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (una parte de la "DIB empaquetada") contienen valores RGB explícitos o índices en la paleta lógica realizada actualmente. El parámetro debe ser uno de los siguientes valores:

- DIB_PAL_COLORS La tabla de colores consta de una matriz de índices de 16 bits.

- DIB_RGB_COLORS La tabla de colores contiene valores RGB literales.

*lpPackedDIB*<br/>
Apunta a un DIB empaquetado `BITMAPINFO` que consta de una estructura seguida inmediatamente de una matriz de bytes que define los píxeles del mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El pincel se puede seleccionar posteriormente para cualquier contexto de dispositivo que admita operaciones ráster.

Las dos versiones difieren en la forma en que usted maneja el DIB:

- En la primera versión, para obtener un identificador `GlobalAlloc` para el DIB se llama a la función de Windows para asignar un bloque de memoria global y, a continuación, rellenar la memoria con el DIB empaquetado.

- En la segunda versión, no `GlobalAlloc` es necesario llamar para asignar memoria para el DIB empaquetado.

Un DIB empaquetado consta `BITMAPINFO` de una estructura de datos seguida inmediatamente por la matriz de bytes que define los píxeles del mapa de bits. Los mapas de bits utilizados como patrones de relleno deben ser de 8 píxeles por 8 píxeles. Si el mapa de bits es más grande, Windows crea un patrón de relleno utilizando solo los bits correspondientes a las primeras 8 filas y 8 columnas de píxeles en la esquina superior izquierda del mapa de bits.

Cuando una aplicación selecciona un pincel de patrón DIB de dos colores en un contexto de dispositivo monocromo, Windows ignora los colores especificados en el DIB y, en su lugar, muestra el pincel de patrón utilizando el texto actual y los colores de fondo del contexto del dispositivo. Los píxeles asignados al primer color (en el desplazamiento 0 en la tabla de colores DIB) del DIB se muestran utilizando el color del texto. Los píxeles asignados al segundo color (en el desplazamiento 1 de la tabla de colores) se muestran con el color de fondo.

Para obtener información sobre el uso de las siguientes funciones de Windows, consulte el Windows SDK:

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Esta función se proporciona solo para la compatibilidad con aplicaciones escritas `CreateDIBPatternBrushPt` para versiones de Windows anteriores a 3.0; utilizar la función.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Esta función se debe utilizar para aplicaciones basadas en Win32.)

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush::CreateHatchBrush

Inicializa un pincel con el patrón sombreado y el color especificados.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el estilo de sombreado del pincel. Puede ser cualquiera de los siguientes valores:

- HS_BDIAGONAL escotilla hacia abajo (de izquierda a derecha) a 45 grados

- HS_CROSS rayado horizontal y vertical

- HS_DIAGCROSS Crosshatch a 45 grados

- HS_FDIAGONAL escotilla hacia arriba (de izquierda a derecha) a 45 grados

- HS_HORIZONTAL escotilla horizontal

- HS_VERTICAL escotilla vertical

*crColor*<br/>
Especifica el color de primer plano del pincel como un color RGB (el color de los sombreados). Consulte [COLORREF](/windows/win32/gdi/colorref) en el Windows SDK para obtener más información.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El pincel se puede seleccionar posteriormente como el pincel actual para cualquier contexto de dispositivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush::CreatePatternBrush

Inicializa un pincel con un patrón especificado por un mapa de bits.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parámetros

*pBitmap*<br/>
Identifica un mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El pincel se puede seleccionar posteriormente para cualquier contexto de dispositivo que admita operaciones ráster. El mapa de bits identificado por *pBitmap* normalmente se inicializa mediante la función [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)o [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) .

Los mapas de bits utilizados como patrones de relleno deben ser de 8 píxeles por 8 píxeles. Si el mapa de bits es más grande, Windows solo usará los bits correspondientes a las primeras 8 filas y columnas de píxeles en la esquina superior izquierda del mapa de bits.

Un pincel de patrón se puede eliminar sin afectar al mapa de bits asociado. Esto significa que el mapa de bits se puede utilizar para crear cualquier número de pinceles de patrón.

Un pincel creado con un mapa de bits monocromo (1 plano de color, 1 bit por píxel) se dibuja utilizando el texto actual y los colores de fondo. Los píxeles representados por un bit establecido en 0 se dibujan con el color de texto actual. Los píxeles representados por un bit establecido en 1 se dibujan con el color de fondo actual.

Para obtener información sobre el uso de [CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush), una función de Windows, consulte el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush::CreateSolidBrush

Inicializa un pincel con un color sólido especificado.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parámetros

*crColor*<br/>
Estructura [COLORREF](/windows/win32/gdi/colorref) que especifica el color del pincel. El color especifica un valor RGB y se puede construir con la macro RGB en WINDOWS. H.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El pincel se puede seleccionar posteriormente como el pincel actual para cualquier contexto de dispositivo.

Cuando una aplicación ha terminado `CreateSolidBrush`de usar el pincel creado por , debe seleccionar el pincel fuera del contexto del dispositivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CBrush::CBrush](#cbrush).

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush

Inicializa un color de pincel.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica un índice de color. Este valor corresponde al color utilizado para pintar uno de los 21 elementos de la ventana. Consulte [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) en el Windows SDK para obtener una lista de valores.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El pincel se puede seleccionar posteriormente como el pincel actual para cualquier contexto de dispositivo.

Cuando una aplicación ha terminado `CreateSysColorBrush`de usar el pincel creado por , debe seleccionar el pincel fuera del contexto del dispositivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a>CBrush::FromHandle

Devuelve un puntero `CBrush` a un objeto cuando se le da un identificador a un objeto [HBRUSH de](#operator_hbrush) Windows.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parámetros

*hBrush*<br/>
MANO a un pincel GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero `CBrush` a un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si `CBrush` un objeto aún no está asociado `CBrush` al identificador, se crea y adjunta un objeto temporal. Este `CBrush` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos. En este momento, se eliminan todos los objetos gráficos temporales. En otras palabras, el objeto temporal sólo es válido durante el procesamiento de un mensaje de ventana.

Para obtener más información sobre el uso de objetos gráficos, vea [Objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CBrush::CBrush](#cbrush).

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush::GetLogBrush

Llame a esta función miembro para recuperar la `LOGBRUSH` estructura.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parámetros

*pLogBrush*<br/>
Apunta a una estructura [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) que contiene información sobre el pincel.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente y *pLogBrush* es un puntero válido, el valor devuelto es el número de bytes almacenados en el búfer.

Si la función se realiza correctamente y *pLogBrush* es NULL, el valor devuelto es el número de bytes necesarios para contener la información que la función almacenaría en el búfer.

Si se produce un error en la función, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

La `LOGBRUSH` estructura define el estilo, el color y el patrón de un pincel.

Por ejemplo, `GetLogBrush` llame para que coincida con el color o patrón determinado de un mapa de bits.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush::operador HBRUSH

Utilice este operador para obtener el identificador `CBrush` GDI de Windows adjunto del objeto.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un identificador para `CBrush` el objeto GDI de Windows representado por el objeto; NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de conversión, que admite el uso directo de un objeto HBRUSH.

Para obtener más información sobre el uso de objetos gráficos, vea [Objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Clase CDC](../../mfc/reference/cdc-class.md)
