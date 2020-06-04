---
title: Clase CPen
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
ms.openlocfilehash: e15dc53fafa0d80f1b52b3fe77f3635c592a4346
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364080"
---
# <a name="cpen-class"></a>Clase CPen

Encapsula un lápiz de la Interfaz de dispositivo gráfico (GDI) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPen : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPen::CPen](#cpen)|Construye un objeto `CPen`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|Crea un lápiz lógico cosmético o geométrico con los atributos de `CPen` estilo, anchura y pincel especificados y lo asocia al objeto.|
|[CPen::CreatePenIndirect](#createpenindirect)|Crea un lápiz con el estilo, el ancho y el color `CPen` especificados en una estructura [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) y lo asocia al objeto.|
|[CPen::FromHandle](#fromhandle)|Devuelve un puntero `CPen` a un objeto cuando se le da un HPEN de Windows.|
|[Cpen::GetExtLogPen](#getextlogpen)|Obtiene una estructura subyacente [EXTLOGPEN.](/windows/win32/api/wingdi/ns-wingdi-extlogpen)|
|[CPen::GetLogPen](#getlogpen)|Obtiene una estructura subyacente [LOGPEN.](/windows/win32/api/wingdi/ns-wingdi-logpen)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPen::operador HPEN](#operator_hpen)|Devuelve el identificador de `CPen` Windows asociado al objeto.|

## <a name="remarks"></a>Observaciones

Para obtener más `CPen`información sobre el uso de , consulte [Objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a>CPen::CPen

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
Especifica el estilo de lápiz. Este parámetro de la primera versión del constructor puede ser uno de los siguientes valores:

- PS_SOLID Crea un lápiz sólido.

- PS_DASH Crea un lápiz discontinuo. Válido sólo cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_DOT Crea un lápiz punteado. Válido sólo cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_DASHDOT Crea un lápiz con guiones y puntos alternos. Válido sólo cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_DASHDOTDOT Crea un lápiz con guiones alternos y puntos dobles. Válido sólo cuando el ancho del lápiz es 1 o menos, en unidades de dispositivo.

- PS_NULL Crea un lápiz nulo.

- PS_INSIDEFRAME Crea un lápiz que dibuja una línea dentro del marco de formas cerradas producidas por `Ellipse`las `Rectangle` `RoundRect`funciones de salida GDI de Windows que especifican un rectángulo delimitador (por ejemplo, las funciones miembro , , , `Pie`y). `Chord` Cuando este estilo se utiliza con funciones de salida GDI de `LineTo` Windows que no especifican un rectángulo delimitador (por ejemplo, la función miembro), el área de dibujo del lápiz no está limitada por un marco.

La segunda versión del `CPen` constructor especifica una combinación de atributos type, style, end cap y join. Los valores de cada categoría deben combinarse mediante el operador OR bit a bit (&#124;). El tipo de lápiz puede ser uno de los siguientes valores:

- PS_GEOMETRIC Crea un lápiz geométrico.

- PS_COSMETIC Crea un lápiz cosmético.

   La segunda versión del `CPen` constructor agrega los siguientes estilos de lápiz para *nPenStyle:*

- PS_ALTERNATE Crea un lápiz que establece cada otro píxel. (Este estilo solo es aplicable a los bolígrafos cosméticos.)

- PS_USERSTYLE Crea un lápiz que utiliza una matriz de estilos proporcionada por el usuario.

   El límite final puede ser uno de los siguientes valores:

- PS_ENDCAP_ROUND las tapas finales son redondas.

- PS_ENDCAP_SQUARE Las tapas finales son cuadradas.

- PS_ENDCAP_FLAT Las tapas finales son planas.

   La combinación puede ser uno de los siguientes valores:

- PS_JOIN_BEVEL se biselan las uniones.

- PS_JOIN_MITER Uniones se inglete cuando están dentro del límite actual establecido por la función [SetMiterLimit.](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) Si la unión supera este límite, se bisela.

- PS_JOIN_ROUND las uniones son redondas.

*nAncho*<br/>
Especifica el ancho del lápiz.

- Para la primera versión del constructor, si este valor es 0, el ancho de las unidades de dispositivo siempre es de 1 píxel, independientemente del modo de asignación.

- Para la segunda versión del constructor, si *nPenStyle* es PS_GEOMETRIC, el ancho se proporciona en unidades lógicas. Si *nPenStyle* es PS_COSMETIC, el ancho debe establecerse en 1.

*crColor*<br/>
Contiene un color RGB para el lápiz.

*pLogBrush*<br/>
Apunta a `LOGBRUSH` una estructura. Si *nPenStyle* es PS_COSMETIC, el `LOGBRUSH` *lbColor* miembro de la estructura especifica el `LOGBRUSH` color del lápiz y el *lbStyle* miembro de la estructura debe establecerse en BS_SOLID. Si *nPenStyle* es PS_GEOMETRIC, todos los miembros deben utilizarse para especificar los atributos de pincel del lápiz.

*nStyleCount*<br/>
Especifica la longitud, en unidades de doble palabra, de la matriz *lpStyle.* Este valor debe ser cero si *nPenStyle* no se PS_USERSTYLE.

*lpStyle*<br/>
Apunta a una matriz de valores de doble palabra. El primer valor especifica la longitud del primer guión en un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio, etc. Este puntero debe ser NULL si *nPenStyle* no es PS_USERSTYLE.

### <a name="remarks"></a>Observaciones

Si utiliza el constructor sin argumentos, `CPen` debe inicializar `CreatePen` `CreatePenIndirect`el `CreateStockObject` objeto resultante con las funciones miembro , o .

Si utiliza el constructor que toma argumentos, no es necesaria ninguna inicialización adicional. El constructor con argumentos puede producir una excepción si se encuentran errores, mientras que el constructor sin argumentos siempre se realizará correctamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a>CPen::CreatePen

Crea un lápiz lógico cosmético o geométrico con los atributos de `CPen` estilo, anchura y pincel especificados y lo asocia al objeto.

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
Especifica el estilo del lápiz. Para obtener una lista de valores posibles, vea el *nPenStyle* parámetro en el [CPen](#cpen) constructor.

*nAncho*<br/>
Especifica el ancho del lápiz.

- Para la primera `CreatePen`versión de , si este valor es 0, el ancho de las unidades de dispositivo siempre es de 1 píxel, independientemente del modo de asignación.

- Para la segunda `CreatePen`versión de , si *nPenStyle* es PS_GEOMETRIC, el ancho se proporciona en unidades lógicas. Si *nPenStyle* es PS_COSMETIC, el ancho debe establecerse en 1.

*crColor*<br/>
Contiene un color RGB para el lápiz.

*pLogBrush*<br/>
Apunta a una estructura [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush) Si *nPenStyle* es `lbColor` PS_COSMETIC, `LOGBRUSH` el miembro de la estructura especifica el color `LOGBRUSH` del lápiz y el *lbStyle* miembro de la estructura debe establecerse en BS_SOLID. Si nPenStyle se PS_GEOMETRIC, todos los miembros deben utilizarse para especificar los atributos de pincel del lápiz.

*nStyleCount*<br/>
Especifica la longitud, en unidades de doble palabra, de la matriz *lpStyle.* Este valor debe ser cero si *nPenStyle* no se PS_USERSTYLE.

*lpStyle*<br/>
Apunta a una matriz de valores de doble palabra. El primer valor especifica la longitud del primer guión en un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio, etc. Este puntero debe ser NULL si *nPenStyle* no es PS_USERSTYLE.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, o cero si se produce un error en el método.

### <a name="remarks"></a>Observaciones

La primera `CreatePen` versión de inicializa un lápiz con el estilo, el ancho y el color especificados. El lápiz se puede seleccionar posteriormente como el lápiz actual para cualquier contexto de dispositivo.

Los plumillas que tienen un ancho superior a 1 píxel siempre deben tener el estilo PS_NULL, PS_SOLID o PS_INSIDEFRAME.

Si un lápiz tiene el estilo PS_INSIDEFRAME y un color que no coincide con un color en la tabla de colores lógica, el lápiz se dibuja con un color tramado. El estilo de pluma PS_SOLID no se puede utilizar para crear un lápiz con un color tramado. El estilo PS_INSIDEFRAME es idéntico al PS_SOLID si el ancho del lápiz es menor o igual que 1.

La segunda `CreatePen` versión de inicializa un lápiz lógico cosmético o geométrico que tiene los atributos de estilo, ancho y pincel especificados. El ancho de una pluma cosmética es siempre 1; el ancho de un lápiz geométrico siempre se especifica en unidades mundiales. Después de que una aplicación crea un lápiz lógico, puede seleccionar ese lápiz en un contexto de dispositivo llamando a la función [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) . Después de seleccionar un lápiz en un contexto de dispositivo, se puede utilizar para dibujar líneas y curvas.

- Si *nPenStyle* es PS_COSMETIC y PS_USERSTYLE, las entradas de la matriz *lpStyle* especifican longitudes de guiones y espacios en unidades de estilo. Una unidad de estilo se define mediante el dispositivo en el que se utiliza el lápiz para dibujar una línea.

- Si *nPenStyle* es PS_GEOMETRIC y PS_USERSTYLE, las entradas de la matriz *lpStyle* especifican longitudes de guiones y espacios en unidades lógicas.

- Si *nPenStyle* se PS_ALTERNATE, se omite la unidad de estilo y se establecen todos los demás píxeles.

Cuando una aplicación ya no requiere un lápiz determinado, debe llamar a la [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro o destruir el `CPen` objeto para que el recurso ya no está en uso. Una aplicación no debe eliminar un lápiz cuando el lápiz está seleccionado en un contexto de dispositivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen::CreatePenIndirect

Inicializa un lápiz que tiene el estilo, el ancho y el color indicados en la estructura a la que apunta *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parámetros

*lpLogPen*<br/>
Apunta a la estructura [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) de Windows que contiene información sobre el lápiz.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Los plumillas que tienen un ancho superior a 1 píxel siempre deben tener el estilo PS_NULL, PS_SOLID o PS_INSIDEFRAME.

Si un lápiz tiene el estilo PS_INSIDEFRAME y un color que no coincide con un color en la tabla de colores lógica, el lápiz se dibuja con un color tramado. El estilo PS_INSIDEFRAME es idéntico al PS_SOLID si el ancho del lápiz es menor o igual que 1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a>CPen::FromHandle

Devuelve un puntero `CPen` a un objeto dado un identificador a un objeto de lápiz GDI de Windows.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parámetros

*hPen*<br/>
`HPEN`mango a la pluma GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero `CPen` a un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si no hay un objeto `CPen` asociado al identificador, se crea y asocia un objeto `CPen` temporal. Este `CPen` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos gráficos temporales. En otras palabras, el objeto temporal sólo es válido durante el procesamiento de un mensaje de ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a>Cpen::GetExtLogPen

Obtiene una `EXTLOGPEN` estructura subyacente.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parámetros

*pLogPen*<br/>
Apunta a una estructura [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) que contiene información sobre el lápiz.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La `EXTLOGPEN` estructura define los atributos de estilo, ancho y pincel de un lápiz. Por ejemplo, `GetExtLogPen` llame para que coincida con el estilo particular de un lápiz.

Consulte los temas siguientes en el Windows SDK para obtener información acerca de los atributos de lápiz:

- [Getobject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Ejemplo

En el ejemplo de `GetExtLogPen` código siguiente se muestra cómo llamar para recuperar los atributos de un lápiz y, a continuación, crear un nuevo lápiz cosmético con el mismo color.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a>CPen::GetLogPen

Obtiene una `LOGPEN` estructura subyacente.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parámetros

*pLogPen*<br/>
Apunta a una estructura [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) para contener información sobre el lápiz.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La `LOGPEN` estructura define el estilo, el color y el patrón de un lápiz.

Por ejemplo, `GetLogPen` llame para que coincida con el estilo particular de la pluma.

Consulte los temas siguientes en el Windows SDK para obtener información acerca de los atributos de lápiz:

- [Getobject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Ejemplo

En el ejemplo de `GetLogPen` código siguiente se muestra cómo llamar para recuperar un carácter de lápiz y, a continuación, crear un nuevo lápiz sólido con el mismo color.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen::operador HPEN

Obtiene el identificador GDI de `CPen` Windows adjunto del objeto.

```
operator HPEN() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un identificador para `CPen` el objeto GDI de Windows representado por el objeto; NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de fundición, que admite el uso directo de un objeto HPEN.

Para obtener más información sobre el uso de objetos gráficos, consulte el artículo [Objetos gráficos](/windows/win32/gdi/graphic-objects) en Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Consulte también

[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CBrush (clase)](../../mfc/reference/cbrush-class.md)
