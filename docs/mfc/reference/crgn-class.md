---
title: Clase Crgn (
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
ms.openlocfilehash: 66721f34a8ac2b6dac6addcfa04a88b46a37ee60
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916826"
---
# <a name="crgn-class"></a>Clase Crgn (

Encapsula una región de la Interfaz de dispositivo gráfico (GDI) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|Construye un objeto `CRgn`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Establece un `CRgn` objeto de modo que sea equivalente a la Unión de dos objetos `CRgn` especificados.|
|[CRgn::CopyRgn](#copyrgn)|Establece un `CRgn` objeto para que sea una copia de un objeto especificado `CRgn` .|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicializa un `CRgn` objeto con una región elíptica.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializa un `CRgn` objeto con una región elíptica definida por una estructura [Rect](/windows/desktop/api/windef/ns-windef-tagrect) .|
|[CRgn::CreateFromData](#createfromdata)|Crea una región a partir de los datos de la región y la transformación especificados.|
|[CRgn::CreateFromPath](#createfrompath)|Crea una región a partir de la ruta de acceso que está seleccionada en el contexto de dispositivo especificado.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicializa un `CRgn` objeto con una región poligonal. El sistema cierra automáticamente el polígono, si es necesario, dibujando una línea desde el último vértice hasta el primero.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicializa un `CRgn` objeto con una región que se compone de una serie de polígonos cerrados. Los polígonos pueden estar separados o pueden superponerse.|
|[CRgn::CreateRectRgn](#createrectrgn)|Inicializa un `CRgn` objeto con una región rectangular.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializa un `CRgn` objeto con una región rectangular definida por una estructura [Rect](/windows/desktop/api/windef/ns-windef-tagrect) .|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicializa un `CRgn` objeto con una región rectangular con esquinas redondeadas.|
|[CRgn::EqualRgn](#equalrgn)|Comprueba dos `CRgn` objetos para determinar si son equivalentes.|
|[CRgn::FromHandle](#fromhandle)|Devuelve un puntero a un `CRgn` objeto cuando se proporciona un identificador a una región de Windows.|
|[CRgn::GetRegionData](#getregiondata)|Rellena el búfer especificado con datos que describen la región especificada.|
|[CRgn::GetRgnBox](#getrgnbox)|Recupera las coordenadas del rectángulo delimitador de un `CRgn` objeto.|
|[CRgn::OffsetRgn](#offsetrgn)|Mueve un `CRgn` objeto por los desplazamientos especificados.|
|[CRgn::PtInRegion](#ptinregion)|Determina si un punto especificado se encuentra en la región.|
|[CRgn::RectInRegion](#rectinregion)|Determina si alguna parte del rectángulo especificado está dentro de los límites de la región.|
|[CRgn::SetRectRgn](#setrectrgn)|Establece el `CRgn` objeto en la región rectangular especificada.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[Crgn (:: Operator HRGN](#operator_hrgn)|Devuelve el identificador de Windows contenido en `CRgn` el objeto.|

## <a name="remarks"></a>Comentarios

Una región es un área elíptica o poligonal dentro de una ventana. Para usar regiones, se usan las funciones miembro de clase `CRgn` con las funciones de recorte definidas como miembros `CDC`de la clase.

Las funciones miembro de `CRgn` crean, modifican y recuperan información sobre el objeto region para el que se les llama.

Para obtener más información sobre `CRgn`el uso de, vea [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="combinergn"></a>Crgn (:: CombineRgn

Crea una nueva región de GDI mediante la combinación de dos regiones existentes.

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
Especifica la operación que se va a realizar al combinar las dos regiones de origen. Puede ser cualquiera de los siguientes valores:

- RGN_AND usa áreas superpuestas de ambas regiones (intersección).

- RGN_COPY crea una copia de la región 1 (identificada mediante *pRgn1*).

- RGN_DIFF crea una región que se compone de las áreas de la región 1 (identificadas por *pRgn1*) que no forman parte de la región 2 (identificada por *pRgn2*).

- RGN_OR combina ambas regiones en su totalidad (Unión).

- RGN_XOR combina ambas regiones pero quita las áreas superpuestas.

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:

- COMPLEXREGION nueva región tiene bordes superpuestos.

- No se pudo crear la nueva región.

- NULLREGION nueva región está vacía.

- SIMPLEREGION nueva región no tiene bordes superpuestos.

### <a name="remarks"></a>Comentarios

Las regiones se combinan según lo especificado por *nCombineMode*.

Las dos regiones especificadas se combinan y el identificador de región resultante se almacena en `CRgn` el objeto. Por lo tanto, cualquier región almacenada `CRgn` en el objeto se reemplaza por la región combinada.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Use [CopyRgn](#copyrgn) para copiar simplemente una región en otra región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>Crgn (:: CopyRgn

Copia la región definida por *pRgnSrc* en el `CRgn` objeto.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parámetros

*pRgnSrc*<br/>
Identifica una región existente.

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:

- COMPLEXREGION nueva región tiene bordes superpuestos.

- No se pudo crear la nueva región.

- NULLREGION nueva región está vacía.

- SIMPLEREGION nueva región no tiene bordes superpuestos.

### <a name="remarks"></a>Comentarios

La nueva región reemplaza la región previamente almacenada en `CRgn` el objeto. Esta función es un caso especial de la función miembro [CombineRgn](#combinergn) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [crgn (:: CreateEllipticRgn](#createellipticrgn).

##  <a name="createellipticrgn"></a>Crgn (:: CreateEllipticRgn

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

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La región se define mediante el rectángulo delimitador especificado por *x1*, *Y1*, *x2*e *Y2*. La región se almacena en el `CRgn` objeto.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Cuando haya terminado de usar una región creada con la `CreateEllipticRgn` función, una aplicación debe seleccionar la región fuera del contexto del dispositivo y usar la `DeleteObject` función para quitarla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

Crea una región elíptica.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una `RECT` estructura o un `CRect` objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha del rectángulo delimitador de la elipse.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La región se define mediante la estructura o el objeto al que apunta *lpRect* y se almacena en `CRgn` el objeto.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Cuando haya terminado de usar una región creada con la `CreateEllipticRgnIndirect` función, una aplicación debe seleccionar la región fuera del contexto del dispositivo y usar la `DeleteObject` función para quitarla.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [crgn (:: CreateRectRgnIndirect](#createrectrgnindirect).

##  <a name="createfromdata"></a>  CRgn::CreateFromData

Crea una región a partir de los datos de la región y la transformación especificados.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parámetros

*lpXForm*<br/>
Apunta a una estructura de datos [XForm](/windows/desktop/api/wingdi/ns-wingdi-tagxform) que define la transformación que se va a realizar en la región. Si este puntero es NULL, se usa la transformación de identidad.

*nCount*<br/>
Especifica el número de bytes al que apunta *pRgnData*.

*pRgnData*<br/>
Apunta a una estructura de datos [rgnData (](/windows/desktop/api/wingdi/ns-wingdi-rgndata) que contiene los datos de la región.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Una aplicación puede recuperar datos para una región llamando a la `CRgn::GetRegionData` función.

##  <a name="createfrompath"></a>Crgn (:: CreateFromPath

Crea una región a partir de la ruta de acceso que está seleccionada en el contexto de dispositivo especificado.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Identifica un contexto de dispositivo que contiene una ruta de acceso cerrada.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El contexto de dispositivo identificado por el parámetro *pDC* debe contener una ruta de acceso cerrada. Después `CreateFromPath` de que convierta una ruta de acceso en una región, Windows descarta la ruta de acceso cerrada del contexto del dispositivo.

##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn

Crea una región poligonal.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parámetros

*lpPoints*<br/>
Apunta a una matriz de `POINT` estructuras o una matriz de `CPoint` objetos. Cada estructura especifica las coordenadas x e y de un vértice del polígono. La `POINT` estructura tiene el formato siguiente:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Especifica el número de `POINT` estructuras u `CPoint` objetos de la matriz a la que apunta *lpPoints*.

*nMode*<br/>
Especifica el modo de relleno para la región. Este parámetro puede ser alternativo o de bobinado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El sistema cierra automáticamente el polígono, si es necesario, dibujando una línea desde el último vértice hasta el primero. La región resultante se almacena en el `CRgn` objeto.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Cuando el modo de relleno de polígonos es alternativo, el sistema rellena el área entre los lados de los polígonos con número impar e par en cada línea de exploración. Es decir, el sistema rellena el área entre el primer y el segundo lado, entre el tercero y el cuarto, y así sucesivamente.

Cuando el modo de relleno de polígonos es bobinado, el sistema utiliza la dirección en la que se dibujó una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en sentido de las agujas del reloj o en el sentido contrario a las agujas del reloj. Siempre que una línea imaginaria dibujada a partir de un área delimitada a la parte externa de una figura pasa a través de un segmento de línea en el sentido de las agujas del reloj, se incrementa el recuento. Cuando la línea pasa a través de un segmento de línea en sentido contrario a las agujas del reloj, se reduce el recuento. El área se rellena si el recuento es distinto de cero cuando la línea llega a la parte externa de la figura.

Cuando una aplicación ha terminado de usar una región creada con `CreatePolygonRgn` la función, debe seleccionar la región fuera del contexto del dispositivo y usar la `DeleteObject` función para quitarla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn

Crea una región que se compone de una serie de polígonos cerrados.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parámetros

*lpPoints*<br/>
Apunta a una matriz de `POINT` estructuras o una matriz de `CPoint` objetos que define los vértices de los polígonos. Cada polígono debe cerrarse explícitamente porque el sistema no los cierra automáticamente. Los polígonos se especifican de forma consecutiva. La `POINT` estructura tiene el formato siguiente:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Apunta a una matriz de enteros. El primer entero especifica el número de vértices del primer polígono de la matriz *lpPoints* , el segundo entero especifica el número de vértices del segundo polígono, y así sucesivamente.

*nCount*<br/>
Especifica el número total de enteros en la matriz *lpPolyCounts* .

*nPolyFillMode*<br/>
Especifica el modo de relleno de polígonos. Este valor puede ser alternativo o de bobinado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La región resultante se almacena en el `CRgn` objeto.

Los polígonos pueden estar separados o pueden superponerse.

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Cuando el modo de relleno de polígonos es alternativo, el sistema rellena el área entre los lados de los polígonos con número impar e par en cada línea de exploración. Es decir, el sistema rellena el área entre el primer y el segundo lado, entre el tercero y el cuarto, y así sucesivamente.

Cuando el modo de relleno de polígonos es bobinado, el sistema utiliza la dirección en la que se dibujó una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en sentido de las agujas del reloj o en el sentido contrario a las agujas del reloj. Siempre que una línea imaginaria dibujada a partir de un área delimitada a la parte externa de una figura pasa a través de un segmento de línea en el sentido de las agujas del reloj, se incrementa el recuento. Cuando la línea pasa a través de un segmento de línea en sentido contrario a las agujas del reloj, se reduce el recuento. El área se rellena si el recuento es distinto de cero cuando la línea llega a la parte externa de la figura.

Cuando una aplicación ha terminado de usar una región creada con `CreatePolyPolygonRgn` la función, debe seleccionar la región fuera del contexto del dispositivo y usar la función miembro [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) para quitarla.

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

Crea una región rectangular que se almacena en el `CRgn` objeto.

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

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Cuando haya terminado de utilizar una región creada por `CreateRectRgn`, una aplicación debe usar la función miembro [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) para quitar la región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Para obtener un ejemplo adicional, vea [crgn (:: CombineRgn](#combinergn).

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

Crea una región rectangular que se almacena en el `CRgn` objeto.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una `RECT` estructura u `CRect` objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha de la región. La `RECT` estructura tiene el formato siguiente:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Cuando haya terminado de utilizar una región creada por `CreateRectRgnIndirect`, una aplicación debe usar la función miembro [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) para quitar la región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn

Crea una región rectangular con esquinas redondeadas que se almacenan en `CRgn` el objeto.

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
Especifica el alto de la elipse utilizada para crear las esquinas redondeadas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El tamaño de una región está limitado a 32.767 por 32.767 unidades lógicas o 64 000 de memoria, lo que sea menor.

Cuando una aplicación ha terminado de usar una región creada con `CreateRoundRectRgn` la función, debe seleccionar la región fuera del contexto del dispositivo y usar la función miembro [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) para quitarla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>Crgn (:: Crgn (

Construye un objeto `CRgn`.

```
CRgn();
```

### <a name="remarks"></a>Comentarios

El `m_hObject` miembro de datos no contiene una región GDI de Windows válida hasta que el objeto se inicializa con una o varias de las `CRgn` otras funciones miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [crgn (:: CreateRoundRectRgn](#createroundrectrgn).

##  <a name="equalrgn"></a>  CRgn::EqualRgn

Determina si la región determinada es equivalente a la región almacenada en `CRgn` el objeto.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parámetros

*pRgn*<br/>
Identifica una región.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las dos regiones son equivalentes; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>  CRgn::FromHandle

Devuelve un puntero a un `CRgn` objeto cuando se proporciona un identificador a una región de Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parámetros

*hRgn*<br/>
Especifica un identificador para una región de Windows.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CRgn` . Si la función no se ha realizado correctamente, el valor devuelto es NULL.

### <a name="remarks"></a>Comentarios

Si un `CRgn` objeto todavía no está asociado al identificador, se crea y `CRgn` se adjunta un objeto temporal. Este objeto `CRgn` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal solo es válido durante el procesamiento de un mensaje de ventana.

##  <a name="getregiondata"></a>  CRgn::GetRegionData

Rellena el búfer especificado con datos que describen la región.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parámetros

*lpRgnData*<br/>
Apunta a una estructura de datos [rgnData (](/windows/desktop/api/wingdi/ns-wingdi-rgndata) que recibe la información. Si este parámetro es NULL, el valor devuelto contiene el número de bytes necesarios para los datos de la región.

*nCount*<br/>
Especifica el tamaño, en bytes, del búfer de *lpRgnData* .

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente y *nCount* especifica un número de bytes adecuado, el valor devuelto siempre es *nCount*. Si se produce un error en la función, o si *nCount* especifica un número de bytes inferior al adecuado, el valor devuelto es 0 (error).

### <a name="remarks"></a>Comentarios

Estos datos incluyen las dimensiones de los rectángulos que componen la región. Esta función se utiliza junto con la `CRgn::CreateFromData` función.

##  <a name="getrgnbox"></a>Crgn (:: GetRgnBox

Recupera las coordenadas del rectángulo delimitador del `CRgn` objeto.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una `RECT` estructura u `CRect` objeto para recibir las coordenadas del rectángulo delimitador. La `RECT` estructura tiene el formato siguiente:

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

- El `CRgn` objeto de error no especifica una región válida.

- La región SIMPLEREGION no tiene bordes superpuestos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [crgn (:: CreatePolygonRgn](#createpolygonrgn).

##  <a name="offsetrgn"></a>Crgn (:: OffsetRgn

Mueve la región almacenada en `CRgn` el objeto por los desplazamientos especificados.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica el número de unidades que se mueven a la izquierda o a la derecha.

*y*<br/>
Especifica el número de unidades para subir o bajar.

*point*<br/>
La coordenada x de *Point* especifica el número de unidades que se mueven a la izquierda o a la derecha. La coordenada y de *Point* especifica el número de unidades que se van a desplace hacia arriba o hacia abajo. El parámetro *Point* puede ser una `POINT` estructura o un `CPoint` objeto.

### <a name="return-value"></a>Valor devuelto

El tipo de la nueva región. Puede ser cualquiera de los siguientes valores:

- La región COMPLEXREGION tiene bordes superpuestos.

- El identificador de la región de ERROR no es válido.

- La región NULLREGION está vacía.

- La región SIMPLEREGION no tiene bordes superpuestos.

### <a name="remarks"></a>Comentarios

La función mueve las unidades de la región *x* a lo largo del eje x y las unidades *y* a lo largo del eje y.

Los valores de las coordenadas de una región deben ser menores o iguales que 32.767 y mayor o igual que-32.768. Los parámetros *x* e *y* se deben elegir con cuidado para evitar las coordenadas de región no válidas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [crgn (:: CreateEllipticRgn](#createellipticrgn).

##  <a name="operator_hrgn"></a>Crgn (:: Operator HRGN

Utilice este operador para obtener el identificador de GDI de Windows asociado `CRgn` del objeto.

```
operator HRGN() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, identificador del objeto GDI de Windows representado por el `CRgn` objeto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este operador es un operador de conversión, que admite el uso directo de un objeto HRGN.

Para obtener más información sobre el uso de objetos gráficos, vea el artículo [objetos gráficos](/windows/desktop/gdi/graphic-objects) en el Windows SDK.

##  <a name="ptinregion"></a>Crgn (::P tInRegion

Comprueba si el punto proporcionado por *x* e y está en la región almacenada en `CRgn` el objeto.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica la coordenada x lógica del punto que se va a probar.

*y*<br/>
Especifica la coordenada y lógica del punto que se va a probar.

*point*<br/>
Las coordenadas x e y del *punto* especifican las coordenadas x e y del punto en el que se va a probar el valor. El parámetro *Point* puede ser una `POINT` estructura o un `CPoint` objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto está en la región; de lo contrario, es 0.

##  <a name="rectinregion"></a>  CRgn::RectInRegion

Determina si alguna parte del rectángulo especificado por *lpRect* se encuentra dentro de los límites de la región almacenada `CRgn` en el objeto.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una `RECT` estructura u `CRect` objeto. La `RECT` estructura tiene el formato siguiente:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si alguna parte del rectángulo especificado está dentro de los límites de la región; de lo contrario, es 0.

##  <a name="setrectrgn"></a>Crgn (:: SetRectRgn

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
Especifica la región rectangular. Puede ser un puntero a una `RECT` estructura o un `CRect` objeto.

### <a name="remarks"></a>Comentarios

Sin embargo, a diferencia de [CreateRectRgn](#createrectrgn), no asigna memoria adicional del montón de aplicación de Windows local. En su lugar, utiliza el espacio asignado para la región almacenada en `CRgn` el objeto. Esto significa que el `CRgn` objeto ya se debe haber inicializado con una región de Windows válida antes `SetRectRgn`de llamar a. Los puntos especificados por *x1*, *Y1*, *x2*e *Y2* especifican el tamaño mínimo del espacio asignado.

Utilice esta función en lugar de la `CreateRectRgn` función miembro para evitar llamadas al administrador de memoria local.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
