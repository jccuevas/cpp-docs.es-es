---
title: Clase CRgn
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 72ab4027880285a3c4cd24d586e163e1e01b98f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368303"
---
# <a name="crgn-class"></a>Clase CRgn

Encapsula una región de la Interfaz de dispositivo gráfico (GDI) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|Construye un objeto `CRgn`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Establece `CRgn` un objeto para que sea equivalente a `CRgn` la unión de dos objetos especificados.|
|[CRgn::CopyRgn](#copyrgn)|Establece `CRgn` un objeto para que sea una `CRgn` copia de un objeto especificado.|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicializa un `CRgn` objeto con una región elíptica.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializa un `CRgn` objeto con una región elíptica definida por una estructura [RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::CreateFromData](#createfromdata)|Crea una región a partir de la región y los datos de transformación especificados.|
|[CRgn::CreateFromPath](#createfrompath)|Crea una región a partir de la ruta de acceso seleccionada en el contexto del dispositivo especificado.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicializa un `CRgn` objeto con una región poligonal. El sistema cierra el polígono automáticamente, si es necesario, dibujando una línea desde el último vértice hasta el primero.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicializa un `CRgn` objeto con una región que consta de una serie de polígonos cerrados. Los polígonos pueden estar desarticulados o pueden superponerse.|
|[CRgn::CreateRectRgn](#createrectrgn)|Inicializa un `CRgn` objeto con una región rectangular.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializa un `CRgn` objeto con una región rectangular definida por una referencia [RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicializa un `CRgn` objeto con una región rectangular con esquinas redondeadas.|
|[CRgn::EqualRgn](#equalrgn)|Comprueba dos `CRgn` objetos para determinar si son equivalentes.|
|[CRgn::FromHandle](#fromhandle)|Devuelve un puntero `CRgn` a un objeto cuando se le da un identificador a una región de Windows.|
|[CRgn::GetRegionData](#getregiondata)|Rellena el búfer especificado con datos que describen la región especificada.|
|[CRgn::GetRgnBox](#getrgnbox)|Recupera las coordenadas del rectángulo delimitador `CRgn` de un objeto.|
|[CRgn::OffsetRgn](#offsetrgn)|Mueve `CRgn` un objeto por los desplazamientos especificados.|
|[CRgn::PtInRegion](#ptinregion)|Determina si un punto especificado está en la región.|
|[CRgn::RectInRegion](#rectinregion)|Determina si alguna parte de un rectángulo especificado está dentro de los límites de la región.|
|[CRgn::SetRectRgn](#setrectrgn)|Establece `CRgn` el objeto en la región rectangular especificada.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRgn::operador HRGN](#operator_hrgn)|Devuelve el identificador de `CRgn` Windows contenido en el objeto.|

## <a name="remarks"></a>Observaciones

Una región es un área elíptica o poligonal dentro de una ventana. Para utilizar regiones, utilice las `CRgn` funciones miembro de la `CDC`clase con las funciones de recorte definidas como miembros de la clase .

Las funciones `CRgn` miembro de crear, modificar y recuperar información sobre el objeto de región para el que se llaman.

Para obtener más `CRgn`información sobre el uso de , consulte [Objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a>CRgn::CombineRgn

Crea una nueva región GDI combinando dos regiones existentes.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>Parámetros

*pRgn1*<br/>
Identifica una región existente.

*pRgn2*<br/>
Identifica una región existente.

*nCombineMode*<br/>
Especifica la operación que se realizará al combinar las dos regiones de origen. Puede ser cualquiera de los siguientes valores:

- RGN_AND Utiliza áreas superpuestas de ambas regiones (intersección).

- RGN_COPY Crea una copia de la región 1 (identificada por *pRgn1*).

- RGN_DIFF Crea una región que consta de las áreas de la región 1 (identificadas por *pRgn1*) que no forman parte de la región 2 (identificada por *pRgn2*).

- RGN_OR Combina ambas regiones en su totalidad (unión).

- RGN_XOR Combina ambas regiones pero elimina las áreas superpuestas.

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:

- COMPLEXREGION Nueva región tiene bordes superpuestos.

- ERROR No se ha creado ninguna nueva región.

- NULLREGION Nueva región está vacía.

- SIMPLEREGION Nueva región no tiene bordes superpuestos.

### <a name="remarks"></a>Observaciones

Las regiones se combinan según lo especificado por *nCombineMode*.

Las dos regiones especificadas se combinan y el `CRgn` identificador de región resultante se almacena en el objeto. Por lo tanto, cualquier `CRgn` región que se almacena en el objeto se reemplaza por la región combinada.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Utilice [CopyRgn](#copyrgn) para copiar simplemente una región en otra región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a>CRgn::CopyRgn

Copia la región definida por *pRgnSrc* en el `CRgn` objeto.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parámetros

*pRgnSrc*<br/>
Identifica una región existente.

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:

- COMPLEXREGION Nueva región tiene bordes superpuestos.

- ERROR No se ha creado ninguna nueva región.

- NULLREGION Nueva región está vacía.

- SIMPLEREGION Nueva región no tiene bordes superpuestos.

### <a name="remarks"></a>Observaciones

La nueva región reemplaza la región `CRgn` almacenada anteriormente en el objeto. Esta función es un caso especial de la [CombineRgn](#combinergn) función miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a>CRgn::CreateEllipticRgn

Crea una región elíptica.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parámetros

*x1*<br/>
Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.

*y1*<br/>
Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.

*x2*<br/>
Especifica la coordenada x lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.

*y2*<br/>
Especifica la coordenada y lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La región se define mediante el rectángulo delimitador especificado por *x1*, *y1*, *x2*e *y2*. La región se `CRgn` almacena en el objeto.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Cuando haya terminado de usar `CreateEllipticRgn` una región creada con la función, una `DeleteObject` aplicación debe seleccionar la región fuera del contexto del dispositivo y utilizar la función para quitarla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect

Crea una región elíptica.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `RECT` una `CRect` estructura o a un objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha del rectángulo delimitador de la elipse.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La región se define mediante la estructura u objeto al `CRgn` que apunta *lpRect* y se almacena en el objeto.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Cuando haya terminado de usar `CreateEllipticRgnIndirect` una región creada con la función, una `DeleteObject` aplicación debe seleccionar la región fuera del contexto del dispositivo y utilizar la función para quitarla.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a>CRgn::CreateFromData

Crea una región a partir de la región y los datos de transformación especificados.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parámetros

*lpXForm*<br/>
Apunta a una estructura de ata [XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)que define la transformación que se realizará en la región. Si este puntero es NULL, se usa la transformación de identidad.

*nCount*<br/>
Especifica el número de bytes a los que apunta *pRgnData*.

*pRgnData*<br/>
Apunta a una estructura de datos [RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata) que contiene los datos de región.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Una aplicación puede recuperar datos de `CRgn::GetRegionData` una región llamando a la función.

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a>CRgn::CreateFromPath

Crea una región a partir de la ruta de acceso seleccionada en el contexto del dispositivo especificado.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Identifica un contexto de dispositivo que contiene una ruta de acceso cerrada.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El contexto de dispositivo identificado por el parámetro *pDC* debe contener una ruta de acceso cerrada. Después `CreateFromPath` de convertir una ruta de acceso en una región, Windows descarta la ruta de acceso cerrada del contexto del dispositivo.

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn

Crea una región poligonal.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parámetros

*lpPoints*<br/>
Apunta a una `POINT` matriz de estructuras o a una matriz de `CPoint` objetos. Cada estructura especifica la coordenada x y la coordenada y de un vértice del polígono. La `POINT` estructura tiene la siguiente forma:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Especifica el número `POINT` de `CPoint` estructuras u objetos de la matriz a la que apunta *lpPoints*.

*nMode*<br/>
Especifica el modo de llenado de la región. Este parámetro puede ser ALTERNATE o WINDING.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El sistema cierra el polígono automáticamente, si es necesario, dibujando una línea desde el último vértice hasta el primero. La región resultante se `CRgn` almacena en el objeto.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Cuando el modo de relleno de polígonos es ALTERNATE, el sistema rellena el área entre los lados de polígono sin números impares e pares en cada línea de exploración. Es decir, el sistema llena el área entre el primer y el segundo lado, entre el tercer y el cuarto lado, y así sucesivamente.

Cuando el modo de relleno de polígonos es WINDING, el sistema utiliza la dirección en la que se dibujó una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en el sentido de las agujas del reloj o en el sentido contrario a las agujas del reloj. Cada vez que una línea imaginaria dibujada desde un área cerrada hasta el exterior de una figura pasa a través de un segmento de línea en el sentido de las agujas del reloj, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea en sentido contrario a las agujas del reloj, el recuento se reduce. El área se rellena si el recuento es distinto de cero cuando la línea alcanza el exterior de la figura.

Cuando una aplicación ha terminado de `CreatePolygonRgn` usar una región creada con la función, debe seleccionar la región fuera del contexto del dispositivo y usar la `DeleteObject` función para quitarla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn

Crea una región que consta de una serie de polígonos cerrados.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parámetros

*lpPoints*<br/>
Apunta a una `POINT` matriz de estructuras o a una matriz de `CPoint` objetos que define los vértices de los polígonos. Cada polígono debe cerrarse explícitamente porque el sistema no los cierra automáticamente. Los polígonos se especifican consecutivamente. La `POINT` estructura tiene la siguiente forma:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Apunta a una matriz de enteros. El primer entero especifica el número de vértices en el primer polígono de la matriz *lpPoints,* el segundo entero especifica el número de vértices en el segundo polígono, y así sucesivamente.

*nCount*<br/>
Especifica el número total de enteros en la matriz *lpPolyCounts.*

*nPolyFillMode*<br/>
Especifica el modo de relleno de polígonos. Este valor puede ser ALTERNATE o WINDING.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La región resultante se `CRgn` almacena en el objeto.

Los polígonos pueden estar desarticulados o pueden superponerse.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Cuando el modo de relleno de polígonos es ALTERNATE, el sistema rellena el área entre los lados de polígono sin números impares e pares en cada línea de exploración. Es decir, el sistema llena el área entre el primer y el segundo lado, entre el tercer y el cuarto lado, y así sucesivamente.

Cuando el modo de relleno de polígonos es WINDING, el sistema utiliza la dirección en la que se dibujó una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en el sentido de las agujas del reloj o en el sentido contrario a las agujas del reloj. Cada vez que una línea imaginaria dibujada desde un área cerrada hasta el exterior de una figura pasa a través de un segmento de línea en el sentido de las agujas del reloj, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea en sentido contrario a las agujas del reloj, el recuento se reduce. El área se rellena si el recuento es distinto de cero cuando la línea alcanza el exterior de la figura.

Cuando una aplicación ha terminado de `CreatePolyPolygonRgn` usar una región creada con la función, debe seleccionar la región fuera del contexto del dispositivo y usar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitarlo.

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a>CRgn::CreateRectRgn

Crea una región rectangular que `CRgn` se almacena en el objeto.

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parámetros

*x1*<br/>
Especifica la coordenada x lógica de la esquina superior izquierda de la región.

*y1*<br/>
Especifica la coordenada y lógica de la esquina superior izquierda de la región.

*x2*<br/>
Especifica la coordenada x lógica de la esquina inferior derecha de la región.

*y2*<br/>
Especifica la coordenada y lógica de la esquina inferior derecha de la región.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Cuando haya terminado de usar `CreateRectRgn`una región creada por , una aplicación debe usar la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitar la región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Para obtener un ejemplo adicional, vea [CRgn::CombineRgn](#combinergn).

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect

Crea una región rectangular que `CRgn` se almacena en el objeto.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `RECT` una `CRect` estructura u objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha de la región. La `RECT` estructura tiene la siguiente forma:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Cuando haya terminado de usar `CreateRectRgnIndirect`una región creada por , una aplicación debe usar la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitar la región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn

Crea una región rectangular con esquinas `CRgn` redondeadas que se almacenan en el objeto.

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>Parámetros

*x1*<br/>
Especifica la coordenada x lógica de la esquina superior izquierda de la región.

*y1*<br/>
Especifica la coordenada y lógica de la esquina superior izquierda de la región.

*x2*<br/>
Especifica la coordenada x lógica de la esquina inferior derecha de la región.

*y2*<br/>
Especifica la coordenada y lógica de la esquina inferior derecha de la región.

*x3*<br/>
Especifica el ancho de la elipse utilizada para crear las esquinas redondeadas.

*y3*<br/>
Especifica la altura de la elipse utilizada para crear las esquinas redondeadas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64K de memoria, lo que sea más pequeño.

Cuando una aplicación ha terminado de `CreateRoundRectRgn` usar una región creada con la función, debe seleccionar la región fuera del contexto del dispositivo y usar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a>CRgn::CRgn

Construye un objeto `CRgn`.

```
CRgn();
```

### <a name="remarks"></a>Observaciones

El `m_hObject` miembro de datos no contiene una región GDI de Windows válida `CRgn` hasta que el objeto se inicializa con una o varias de las otras funciones miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateRoundRectRgn](#createroundrectrgn).

## <a name="crgnequalrgn"></a><a name="equalrgn"></a>CRgn::EqualRgn

Determina si la región dada es equivalente `CRgn` a la región almacenada en el objeto.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parámetros

*pRgn*<br/>
Identifica una región.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las dos regiones son equivalentes; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a>CRgn::FromHandle

Devuelve un puntero `CRgn` a un objeto cuando se le da un identificador a una región de Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parámetros

*hRgn*<br/>
Especifica un identificador para una región de Windows.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CRgn` . Si la función no se realizó correctamente, el valor devuelto es NULL.

### <a name="remarks"></a>Observaciones

Si `CRgn` un objeto aún no está asociado `CRgn` al identificador, se crea y adjunta un objeto temporal. Este `CRgn` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal sólo es válido durante el procesamiento de un mensaje de ventana.

## <a name="crgngetregiondata"></a><a name="getregiondata"></a>CRgn::GetRegionData

Rellena el búfer especificado con datos que describen la región.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parámetros

*lpRgnData*<br/>
Señala a una estructura de datos [RGNDATA](/windows/win32/api/wingdi/ns-wingdi-rgndata) que recibe la información. Si este parámetro es NULL, el valor devuelto contiene el número de bytes necesarios para los datos de región.

*nCount*<br/>
Especifica el tamaño, en bytes, del búfer *lpRgnData.*

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente y *nCount* especifica un número adecuado de bytes, el valor devuelto siempre es *nCount*. Si se produce un error en la función, o si *nCount* especifica un número de bytes inferior al adecuado, el valor devuelto es 0 (error).

### <a name="remarks"></a>Observaciones

Estos datos incluyen las dimensiones de los rectángulos que componen la región. Esta función se utiliza `CRgn::CreateFromData` junto con la función.

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a>CRgn::GetRgnBox

Recupera las coordenadas del rectángulo delimitador `CRgn` del objeto.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `RECT` una `CRect` estructura u objeto para recibir las coordenadas del rectángulo delimitador. La `RECT` estructura tiene la siguiente forma:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región. Puede ser cualquiera de los siguientes valores:

- La región COMPLEXREGION tiene bordes superpuestos.

- La región NULLREGION está vacía.

- El `CRgn` objeto ERROR no especifica una región válida.

- La región SIMPLEREGION no tiene bordes superpuestos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreatePolygonRgn](#createpolygonrgn).

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a>CRgn::OffsetRgn

Mueve la región `CRgn` almacenada en el objeto por los desplazamientos especificados.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Especifica el número de unidades que se moverán a la izquierda o a la derecha.

*y y*<br/>
Especifica el número de unidades que se moverán hacia arriba o hacia abajo.

*Punto*<br/>
La coordenada x del *punto* especifica el número de unidades que se moverán a la izquierda o a la derecha. La coordenada y del *punto* especifica el número de unidades que se moverán hacia arriba o hacia abajo. El parámetro *point* puede `POINT` ser `CPoint` una estructura o un objeto.

### <a name="return-value"></a>Valor devuelto

Tipo de la nueva región. Puede ser cualquiera de los siguientes valores:

- La región COMPLEXREGION tiene bordes superpuestos.

- El identificador de región ERROR no es válido.

- La región NULLREGION está vacía.

- La región SIMPLEREGION no tiene bordes superpuestos.

### <a name="remarks"></a>Observaciones

La función mueve las unidades de región *x* a lo largo del eje X y las unidades *y* a lo largo del eje Y.

Los valores de coordenadas de una región deben ser menores o iguales que 32.767 y mayores o iguales a -32.768. Los parámetros *x* e *y* deben elegirse cuidadosamente para evitar coordenadas de región no válidas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a>CRgn::operador HRGN

Utilice este operador para obtener el identificador `CRgn` GDI de Windows adjunto del objeto.

```
operator HRGN() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un identificador para `CRgn` el objeto GDI de Windows representado por el objeto; NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de conversión, que admite el uso directo de un objeto HRGN.

Para obtener más información sobre el uso de objetos gráficos, consulte el artículo [Objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

## <a name="crgnptinregion"></a><a name="ptinregion"></a>CRgn::PtInRegion

Comprueba si el punto dado por *x* e *y* se encuentra en la región almacenada en el `CRgn` objeto.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Especifica la coordenada x lógica del punto que se va a probar.

*y y*<br/>
Especifica la coordenada y lógica del punto que se va a probar.

*Punto*<br/>
Las coordenadas x e y del *punto* especifican las coordenadas x e y del punto para probar el valor de. El parámetro *point* puede `POINT` ser `CPoint` una estructura o un objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto está en la región; de lo contrario 0.

## <a name="crgnrectinregion"></a><a name="rectinregion"></a>CRgn::RectInRegion

Determina si alguna parte del rectángulo especificado por *lpRect* está dentro `CRgn` de los límites de la región almacenada en el objeto.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `RECT` una `CRect` estructura u objeto. La `RECT` estructura tiene la siguiente forma:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si alguna parte del rectángulo especificado se encuentra dentro de los límites de la región; de lo contrario 0.

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a>CRgn::SetRectRgn

Crea una región rectangular.

```
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*x1*<br/>
Especifica la coordenada x de la esquina superior izquierda de la región rectangular.

*y1*<br/>
Especifica la coordenada y de la esquina superior izquierda de la región rectangular.

*x2*<br/>
Especifica la coordenada x de la esquina inferior derecha de la región rectangular.

*y2*<br/>
Especifica la coordenada y de la esquina inferior derecha de la región rectangular.

*lpRect*<br/>
Especifica la región rectangular. Puede ser un puntero `RECT` a `CRect` una estructura o un objeto.

### <a name="remarks"></a>Observaciones

Sin embargo, a diferencia de [CreateRectRgn,](#createrectrgn)no asigna ninguna memoria adicional del montón de aplicaciones locales de Windows. En su lugar, utiliza el espacio `CRgn` asignado para la región almacenada en el objeto. Esto significa `CRgn` que el objeto ya debe haberse `SetRectRgn`inicializado con una región de Windows válida antes de llamar a . Los puntos dados por *x1*, *y1*, *x2*e *y2* especifican el tamaño mínimo del espacio asignado.

Utilice esta función `CreateRectRgn` en lugar de la función miembro para evitar llamadas al administrador de memoria local.

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
