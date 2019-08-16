---
title: Clase CPen (
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: 952d270acd47b5834a06b731f7875ea2efdd4695
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502949"
---
# <a name="cpen-class"></a>Clase CPen (

Encapsula un lápiz de la Interfaz de dispositivo gráfico (GDI) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPen : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPen::CPen](#cpen)|Construye un objeto `CPen`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|Crea un lápiz cosmético o geométrico lógico con los atributos de estilo, ancho y pincel especificados y lo adjunta al `CPen` objeto.|
|[CPen::CreatePenIndirect](#createpenindirect)|Crea un lápiz con el estilo, el ancho y el color especificados en una estructura [logpen (](/windows/win32/api/wingdi/ns-wingdi-logpen) y lo adjunta al `CPen` objeto.|
|[CPen::FromHandle](#fromhandle)|Devuelve un puntero a un `CPen` objeto cuando se proporciona un HPEN de Windows.|
|[CPen::GetExtLogPen](#getextlogpen)|Obtiene una estructura subyacente de [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) .|
|[CPen::GetLogPen](#getlogpen)|Obtiene una estructura subyacente de [logpen (](/windows/win32/api/wingdi/ns-wingdi-logpen) .|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPen (:: Operator HPEN](#operator_hpen)|Devuelve el identificador de Windows asociado al `CPen` objeto.|

## <a name="remarks"></a>Comentarios

Para obtener más información sobre `CPen`el uso de, vea [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cpen"></a>  CPen::CPen

Construye un objeto `CPen`.

```
CPen();

CPen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

CPen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parámetros

*nPenStyle*<br/>
Especifica el estilo del lápiz. Este parámetro de la primera versión del constructor puede ser uno de los valores siguientes:

- PS_SOLID crea un lápiz sólido.

- PS_DASH crea un lápiz discontinuo. Solo es válido cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_DOT crea un lápiz punteado. Solo es válido cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_DASHDOT crea un lápiz con guiones y puntos alternos. Solo es válido cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_DASHDOTDOT crea un lápiz con guiones alternativos y puntos dobles. Solo es válido cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_NULL crea un lápiz nulo.

- PS_INSIDEFRAME crea un lápiz que dibuja una línea dentro del marco de las formas cerradas producidas por las funciones de salida de Windows GDI que especifican un rectángulo delimitador ( `RoundRect`por `Pie`ejemplo, `Ellipse`, `Rectangle`,, y `Chord`funciones miembro). Cuando este estilo se utiliza con funciones de salida de Windows GDI que no especifican un rectángulo delimitador (por `LineTo` ejemplo, la función miembro), el área de dibujo del lápiz no está limitada por un marco.

La segunda versión del `CPen` constructor especifica una combinación de tipo, estilo, extremo final y atributos de combinación. Los valores de cada categoría se deben combinar mediante el operador bit a bit OR&#124;(). El tipo de lápiz puede ser uno de los siguientes valores:

- PS_GEOMETRIC crea un lápiz geométrico.

- PS_COSMETIC crea un lápiz cosmético.

   La segunda versión del `CPen` constructor agrega los siguientes estilos de lápiz para *nPenStyle*:

- PS_ALTERNATE crea un lápiz que establece todos los demás píxeles. (Este estilo solo es aplicable a los lápices cosméticos).

- PS_USERSTYLE crea un lápiz que usa una matriz de estilo proporcionada por el usuario.

   El extremo final puede ser uno de los siguientes valores:

- Los extremos de PS_ENDCAP_ROUND se redondean.

- Los extremos finales de PS_ENDCAP_SQUARE son cuadrados.

- Los extremos de PS_ENDCAP_FLAT son planos.

   La combinación puede ser uno de los valores siguientes:

- Las combinaciones de PS_JOIN_BEVEL están biseladas.

- Las combinaciones de PS_JOIN_MITER se definen en un ángulo cuando están dentro del límite actual establecido por la función [SetMiterLimit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) . Si la combinación supera este límite, está biselado.

- Las combinaciones PS_JOIN_ROUND son round.

*nWidth*<br/>
Especifica el ancho del lápiz.

- En el caso de la primera versión del constructor, si este valor es 0, el ancho de las unidades de dispositivo siempre es 1 píxel, independientemente del modo de asignación.

- En el caso de la segunda versión del constructor, si *nPenStyle* es PS_GEOMETRIC, el ancho se proporciona en unidades lógicas. Si *nPenStyle* es PS_COSMETIC, el ancho debe establecerse en 1.

*crColor*<br/>
Contiene un color RGB para el lápiz.

*pLogBrush*<br/>
Apunta a una `LOGBRUSH` estructura. Si *nPenStyle* es PS_COSMETIC, el miembro *lbColor* de la `LOGBRUSH` estructura especifica el color del lápiz y el miembro *lbStyle* de la `LOGBRUSH` estructura debe establecerse en BS_SOLID. Si *nPenStyle* es PS_GEOMETRIC, todos los miembros deben usarse para especificar los atributos de pincel del lápiz.

*nStyleCount*<br/>
Especifica la longitud, en unidades palabra, de la matriz *lpStyle* . Este valor debe ser cero si *nPenStyle* no es PS_USERSTYLE.

*lpStyle*<br/>
Apunta a una matriz de valores palabra. El primer valor especifica la longitud del primer guión de un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio, etc. Este puntero debe ser NULL si *nPenStyle* no es PS_USERSTYLE.

### <a name="remarks"></a>Comentarios

Si utiliza el constructor sin argumentos `CPen` , debe inicializar el objeto resultante con las `CreatePen`funciones miembro, `CreatePenIndirect`o. `CreateStockObject`

Si usa el constructor que toma argumentos, no es necesario realizar ninguna inicialización adicional. El constructor con argumentos puede producir una excepción si se producen errores, mientras que el constructor sin argumentos siempre se realizará correctamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>  CPen::CreatePen

Crea un lápiz cosmético o geométrico lógico con los atributos de estilo, ancho y pincel especificados y lo adjunta al `CPen` objeto.

```
BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parámetros

*nPenStyle*<br/>
Especifica el estilo del lápiz. Para obtener una lista de los valores posibles, vea el parámetro *nPenStyle* en el constructor [CPen (](#cpen) .

*nWidth*<br/>
Especifica el ancho del lápiz.

- En la primera versión de `CreatePen`, si este valor es 0, el ancho de las unidades de dispositivo siempre es 1 píxel, independientemente del modo de asignación.

- En el caso de la `CreatePen`segunda versión de, si *nPenStyle* es PS_GEOMETRIC, el ancho se proporciona en unidades lógicas. Si *nPenStyle* es PS_COSMETIC, el ancho debe establecerse en 1.

*crColor*<br/>
Contiene un color RGB para el lápiz.

*pLogBrush*<br/>
Apunta a una estructura [logbrush (](/windows/win32/api/wingdi/ns-wingdi-logbrush) . Si *nPenStyle* es PS_COSMETIC, el `lbColor` miembro de la `LOGBRUSH` estructura especifica el color del lápiz y el miembro *lbStyle* de la `LOGBRUSH` estructura debe establecerse en BS_SOLID. Si nPenStyle es PS_GEOMETRIC, todos los miembros deben usarse para especificar los atributos de pincel del lápiz.

*nStyleCount*<br/>
Especifica la longitud, en unidades palabra, de la matriz *lpStyle* . Este valor debe ser cero si *nPenStyle* no es PS_USERSTYLE.

*lpStyle*<br/>
Apunta a una matriz de valores palabra. El primer valor especifica la longitud del primer guión de un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio, etc. Este puntero debe ser NULL si *nPenStyle* no es PS_USERSTYLE.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, o cero si se produce un error en el método.

### <a name="remarks"></a>Comentarios

La primera versión de `CreatePen` Inicializa un lápiz con el estilo, el ancho y el color especificados. Posteriormente, el lápiz se puede seleccionar como el lápiz actual para cualquier contexto de dispositivo.

Los lápices que tienen un ancho mayor que 1 píxel siempre deben tener el estilo PS_NULL, PS_SOLID o PS_INSIDEFRAME.

Si un lápiz tiene el estilo PS_INSIDEFRAME y un color que no coincide con un color de la tabla de colores lógicos, el lápiz se dibuja con un color dipuesto. El estilo de lápiz PS_SOLID no se puede usar para crear un lápiz con un color El estilo PS_INSIDEFRAME es idéntico a PS_SOLID si el ancho del lápiz es menor o igual que 1.

La segunda versión de `CreatePen` Inicializa una plumilla lógica o estética lógica que tiene los atributos de estilo, ancho y pincel especificados. El ancho de un lápiz cosmético siempre es 1; el ancho de un lápiz geométrico siempre se especifica en unidades universales. Después de que una aplicación crea un lápiz lógico, puede seleccionar ese lápiz en un contexto de dispositivo mediante una llamada a la función [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) . Una vez que se selecciona un lápiz en un contexto de dispositivo, se puede usar para dibujar líneas y curvas.

- Si *nPenStyle* es PS_COSMETIC y PS_USERSTYLE, las entradas de la matriz *lpStyle* especifican las longitudes de los guiones y espacios en las unidades de estilo. Una unidad de estilo se define mediante el dispositivo en el que se usa el lápiz para dibujar una línea.

- Si *nPenStyle* es PS_GEOMETRIC y PS_USERSTYLE, las entradas de la matriz *lpStyle* especifican las longitudes de los guiones y espacios en unidades lógicas.

- Si *nPenStyle* es PS_ALTERNATE, se omite la unidad de estilo y se establece el resto de píxeles.

Cuando una aplicación ya no requiere un lápiz determinado, debe llamar a la función miembro [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) o destruir el `CPen` objeto para que el recurso ya no esté en uso. Una aplicación no debe eliminar un lápiz cuando se selecciona el lápiz en un contexto de dispositivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect

Inicializa un lápiz con el estilo, el ancho y el color especificados en la estructura a la que apunta *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parámetros

*lpLogPen*<br/>
Apunta a la estructura [logpen (](/windows/win32/api/Wingdi/ns-wingdi-logpen) de Windows que contiene información sobre el lápiz.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Los lápices que tienen un ancho mayor que 1 píxel siempre deben tener el estilo PS_NULL, PS_SOLID o PS_INSIDEFRAME.

Si un lápiz tiene el estilo PS_INSIDEFRAME y un color que no coincide con un color de la tabla de colores lógicos, el lápiz se dibuja con un color dipuesto. El estilo PS_INSIDEFRAME es idéntico a PS_SOLID si el ancho del lápiz es menor o igual que 1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>  CPen::FromHandle

Devuelve un puntero a un `CPen` objeto dado un identificador a un objeto Pen de Windows GDI.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parámetros

*hPen*<br/>
`HPEN`identificador del lápiz de Windows GDI.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CPen` objeto si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si no hay un objeto `CPen` asociado al identificador, se crea y asocia un objeto `CPen` temporal. Este objeto `CPen` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos gráficos temporales. En otras palabras, el objeto temporal solo es válido durante el procesamiento de un mensaje de ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>  CPen::GetExtLogPen

Obtiene una `EXTLOGPEN` estructura subyacente.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parámetros

*pLogPen*<br/>
Apunta a una estructura [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) que contiene información sobre el lápiz.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La `EXTLOGPEN` estructura define los atributos de estilo, ancho y pincel de un lápiz. Por ejemplo, llame `GetExtLogPen` a para que coincida con el estilo determinado de un lápiz.

Vea los temas siguientes en la Windows SDK para obtener información sobre los atributos de los lápices:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `GetExtLogPen` se muestra cómo llamar a para recuperar los atributos de un lápiz y, a continuación, crear un nuevo lápiz cosmético con el mismo color.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>  CPen::GetLogPen

Obtiene una `LOGPEN` estructura subyacente.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parámetros

*pLogPen*<br/>
Apunta a una estructura [logpen (](/windows/win32/api/wingdi/ns-wingdi-logpen) para que contenga información sobre el lápiz.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La `LOGPEN` estructura define el estilo, el color y el patrón de un lápiz.

Por ejemplo, llame `GetLogPen` a para que coincida con el estilo determinado del lápiz.

Vea los temas siguientes en la Windows SDK para obtener información sobre los atributos de los lápices:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `GetLogPen` se muestra cómo llamar a para recuperar un carácter de lápiz y, a continuación, crear un nuevo lápiz sólido con el mismo color.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>CPen (:: Operator HPEN

Obtiene el identificador de GDI de Windows asociado `CPen` del objeto.

```
operator HPEN() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, identificador del objeto GDI de Windows representado por el `CPen` objeto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este operador es un operador de conversión, que admite el uso directo de un objeto HPEN.

Para obtener más información sobre el uso de objetos gráficos, vea el artículo [objetos gráficos](/windows/win32/gdi/graphic-objects) en Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Vea también

[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CBrush (clase)](../../mfc/reference/cbrush-class.md)
