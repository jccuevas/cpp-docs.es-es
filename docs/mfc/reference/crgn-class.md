---
title: CRgn (clase)
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
ms.openlocfilehash: 74ee046e81e0f55e5550220166c957317c2bf6cd
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178556"
---
# <a name="crgn-class"></a>CRgn (clase)

Encapsula una región de la Interfaz de dispositivo gráfico (GDI) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|Construye un objeto `CRgn`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Establece un `CRgn` objeto para que sea equivalente a la unión de dos especificado `CRgn` objetos.|
|[CRgn::CopyRgn](#copyrgn)|Establece un `CRgn` para que sea una copia de una clase de objeto `CRgn` objeto.|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicializa un `CRgn` objeto con una región elíptica.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializa un `CRgn` objeto con una región elíptica definida por un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura.|
|[CRgn::CreateFromData](#createfromdata)|Crea una región de los datos de transformación y región determinados.|
|[CRgn::CreateFromPath](#createfrompath)|Crea una región de la ruta de acceso que está seleccionado en el contexto de dispositivo determinado.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicializa un `CRgn` objeto con una región poligonal. El sistema cierra el polígono automáticamente, si es necesario, al dibujar una línea desde el último vértice al primero.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicializa un `CRgn` objeto con una región que consta de una serie de polígonos cerrados. Los polígonos pueden no contiguos, o que es posible que se superponen.|
|[CRgn::CreateRectRgn](#createrectrgn)|Inicializa un `CRgn` objeto con una región rectangular.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializa un `CRgn` objeto con una región rectangular definida por un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura.|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicializa un `CRgn` objeto con una región rectangular con esquinas redondeadas.|
|[CRgn::EqualRgn](#equalrgn)|Comprueba dos `CRgn` objetos para determinar si son equivalentes.|
|[CRgn::FromHandle](#fromhandle)|Devuelve un puntero a un `CRgn` objeto cuando se especifica un identificador a una región de Windows.|
|[CRgn::GetRegionData](#getregiondata)|Llena el búfer especificado con los datos que describen la región especificada.|
|[CRgn::GetRgnBox](#getrgnbox)|Recupera las coordenadas del rectángulo delimitador de un `CRgn` objeto.|
|[CRgn::OffsetRgn](#offsetrgn)|Mueve un `CRgn` objeto por los desplazamientos especificados.|
|[CRgn::PtInRegion](#ptinregion)|Determina si un punto especificado está en la región.|
|[CRgn::RectInRegion](#rectinregion)|Determina si cualquier parte de un rectángulo especificado está dentro de los límites de la región.|
|[CRgn::SetRectRgn](#setrectrgn)|Establece el `CRgn` objeto a la región rectangular especificada.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CRgn::operator HRGN](#operator_hrgn)|Devuelve el identificador de Windows contenido en el `CRgn` objeto.|

## <a name="remarks"></a>Comentarios

Una región es un área elíptico o poligonal dentro de una ventana. Para usar las regiones, usa las funciones miembro de clase `CRgn` con las funciones de recorte definidas como miembros de clase `CDC`.

Las funciones miembro de `CRgn` crear, modificar y recuperar información sobre el objeto de región para el que se les llama.

Para obtener más información sobre el uso de `CRgn`, consulte [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="combinergn"></a>  CRgn::CombineRgn

Crea una nueva región GDI mediante la combinación de dos regiones existentes.

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
Especifica la operación se realizará al combinar las regiones de origen de dos. Puede ser cualquiera de los siguientes valores:

- RGN_AND usa las áreas de ambas regiones (intersección) superpuestas.

- RGN_COPY crea una copia de la región 1 (identificado por *pRgn1*).

- RGN_DIFF crea una región que consta de las áreas de la región 1 (identificado por *pRgn1*) que no forman parte de la región 2 (identificado por *pRgn2*).

- RGN_OR combina ambas regiones en su totalidad (unión).

- RGN_XOR combina ambas regiones pero quita las áreas superpuestas.

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:

- COMPLEXREGION nueva región tiene superpuesto en los bordes.

- ERROR que no se creó ninguna nueva región.

- NULLREGION nueva región está vacía.

- SIMPLEREGION nueva región no tiene bordes superpuestos.

### <a name="remarks"></a>Comentarios

Las regiones se combinan según lo especificado por *nCombineMode*.

Especificado de las dos regiones se combinan y el identificador de región resultante se almacena en la `CRgn` objeto. Por lo tanto, cualquier región se almacena en la `CRgn` objeto se sustituye por la región combinada.

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Use [CopyRgn](#copyrgn) copiar simplemente una región en otra región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>  CRgn::CopyRgn

Copia la región definida por *pRgnSrc* en el `CRgn` objeto.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parámetros

*pRgnSrc*<br/>
Identifica una región existente.

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:

- COMPLEXREGION nueva región tiene superpuesto en los bordes.

- ERROR que no se creó ninguna nueva región.

- NULLREGION nueva región está vacía.

- SIMPLEREGION nueva región no tiene bordes superpuestos.

### <a name="remarks"></a>Comentarios

La nueva región reemplaza la región almacenada anteriormente en el `CRgn` objeto. Esta función es un caso especial de la [CombineRgn](#combinergn) función miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateEllipticRgn](#createellipticrgn).

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

Crea una región elíptica.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parámetros

*X1*<br/>
Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.

*y1*<br/>
Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.

*X2*<br/>
Especifica la coordenada x lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.

*y2*<br/>
Especifica la coordenada y lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La región se define por el rectángulo delimitador especificado por *x1*, *y1*, *x2*, y *y2*. La región se almacena en la `CRgn` objeto.

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Cuando ha terminado de usar una región que se creó con la `CreateEllipticRgn` función, una aplicación debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

Crea una región elíptica.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un `RECT` estructura o un `CRect` objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha del rectángulo delimitador de la elipse.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La región se define mediante la estructura o el objeto al que señala *lpRect* y se almacena en la `CRgn` objeto.

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Cuando ha terminado de usar una región que se creó con la `CreateEllipticRgnIndirect` función, una aplicación debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitarlo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).

##  <a name="createfromdata"></a>  CRgn::CreateFromData

Crea una región de los datos de transformación y región determinados.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parámetros

*lpXForm*<br/>
Apunta a un [XFORM](/windows/desktop/api/wingdi/ns-wingdi-tagxform) estructura de datos que define la transformación que se realizará en la región. Si este puntero es NULL, se utiliza la transformación de identidad.

*nCount*<br/>
Especifica el número de bytes que señala *pRgnData*.

*pRgnData*<br/>
Apunta a un [RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-_rgndata) estructura de datos que contiene los datos de la región.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Una aplicación puede recuperar datos de una región mediante una llamada a la `CRgn::GetRegionData` función.

##  <a name="createfrompath"></a>  CRgn::CreateFromPath

Crea una región de la ruta de acceso que está seleccionado en el contexto de dispositivo determinado.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Identifica un contexto de dispositivo que contiene un trayecto cerrado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El contexto de dispositivo identificado por el *pDC* parámetro debe contener un trayecto cerrado. Después de `CreateFromPath` convierte una ruta de acceso en una región, Windows descarta el trayecto cerrado desde el contexto de dispositivo.

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
Señala a una matriz de `POINT` estructuras o una matriz de `CPoint` objetos. Cada estructura especifica la coordenada x y Coordenada y de un vértice del polígono. El `POINT` estructura tiene el formato siguiente:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Especifica el número de `POINT` estructuras o `CPoint` objetos de la matriz señalada por *lpPoints*.

*nMode*<br/>
Especifica el modo de relleno para la región. Este parámetro puede ser texto alternativo o DEVANADO.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El sistema cierra el polígono automáticamente, si es necesario, al dibujar una línea desde el último vértice al primero. La región resultante se almacena en la `CRgn` objeto.

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Cuando el modo de relleno de polígono es alternativo, el sistema rellena el área entre los lados de un polígono pares e impares en cada línea de exploración. Es decir, el sistema rellena el área entre el lado de la primero y segundo, entre el lado de la tercero y cuarto y así sucesivamente.

Cuando el modo de relleno de polígono de DEVANADO, el sistema usa la dirección en la que se dibuja una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en un hacia la derecha o una dirección a la izquierda. Siempre que una línea imaginaria de un área delimitada al exterior de una figura pasa a través de un segmento de línea de las agujas del reloj, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea a la izquierda, el recuento es reducido. Si el recuento es distinto de cero cuando llega a la línea de la parte exterior de la ilustración, se rellena el área.

Cuando una aplicación ha terminado de utilizar una región que se creó con la `CreatePolygonRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn

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
Señala a una matriz de `POINT` estructuras o una matriz de `CPoint` objetos que define los vértices de los polígonos. Cada polígono debe estar cerrado explícitamente porque el sistema no cerrarlos automáticamente. Los polígonos se especifican de forma consecutiva. El `POINT` estructura tiene el formato siguiente:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Apunta a una matriz de enteros. El primer entero especifica el número de vértices del polígono en primera la *lpPoints* matriz, el segundo entero especifica el número de vértices en el polígono segunda y así sucesivamente.

*nCount*<br/>
Especifica el número total de enteros en el *lpPolyCounts* matriz.

*nPolyFillMode*<br/>
Especifica el modo de relleno de polígono. Este valor puede ser alternativa o liquidación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La región resultante se almacena en la `CRgn` objeto.

Los polígonos pueden no contiguos, o que es posible que se superponen.

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Cuando el modo de relleno de polígono es alternativo, el sistema rellena el área entre los lados de un polígono pares e impares en cada línea de exploración. Es decir, el sistema rellena el área entre el lado de la primero y segundo, entre el lado de la tercero y cuarto y así sucesivamente.

Cuando el modo de relleno de polígono de DEVANADO, el sistema usa la dirección en la que se dibuja una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en un hacia la derecha o una dirección a la izquierda. Siempre que una línea imaginaria de un área delimitada al exterior de una figura pasa a través de un segmento de línea de las agujas del reloj, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea a la izquierda, el recuento es reducido. Si el recuento es distinto de cero cuando llega a la línea de la parte exterior de la ilustración, se rellena el área.

Cuando una aplicación ha terminado de utilizar una región que se creó con la `CreatePolyPolygonRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitarlo.

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

Crea un área rectangular que se almacena en la `CRgn` objeto.

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parámetros

*X1*<br/>
Especifica la coordenada x lógica de la esquina superior izquierda de la región.

*y1*<br/>
Especifica la coordenada y lógica de la esquina superior izquierda de la región.

*X2*<br/>
Especifica la coordenada x lógica de la esquina inferior derecha de la región.

*y2*<br/>
Especifica la coordenada y lógica de la esquina inferior derecha de la región.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Cuando ha terminado de usar una región creada por `CreateRectRgn`, una aplicación debe utilizar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitar la región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Para obtener un ejemplo adicional, consulte [CRgn::CombineRgn](#combinergn).

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

Crea un área rectangular que se almacena en la `CRgn` objeto.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un `RECT` estructura o `CRect` objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha de la región. El `RECT` estructura tiene el formato siguiente:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Cuando ha terminado de usar una región creada por `CreateRectRgnIndirect`, una aplicación debe utilizar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitar la región.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn

Crea una región rectangular con esquinas redondeadas que se almacena en la `CRgn` objeto.

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

*X1*<br/>
Especifica la coordenada x lógica de la esquina superior izquierda de la región.

*y1*<br/>
Especifica la coordenada y lógica de la esquina superior izquierda de la región.

*X2*<br/>
Especifica la coordenada x lógica de la esquina inferior derecha de la región.

*y2*<br/>
Especifica la coordenada y lógica de la esquina inferior derecha de la región.

*x3*<br/>
Especifica el ancho de la elipse que se usa para crear las esquinas redondeadas.

*Y3*<br/>
Especifica el alto de la elipse que se usa para crear las esquinas redondeadas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El tamaño de una región se limita a 64 KB de memoria o de unidades lógicas de 32.767 por 32.767, lo que sea menor.

Cuando una aplicación ha terminado de utilizar una región que se creó con la `CreateRoundRectRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función miembro para quitarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>  CRgn::CRgn

Construye un objeto `CRgn`.

```
CRgn();
```

### <a name="remarks"></a>Comentarios

El `m_hObject` miembro de datos no contiene una región de GDI de Windows válida hasta que el objeto se inicializa con uno o varios de los demás `CRgn` funciones miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateRoundRectRgn](#createroundrectrgn).

##  <a name="equalrgn"></a>  CRgn::EqualRgn

Determina si la región especificada es equivalente a la región que se almacenan en la `CRgn` objeto.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parámetros

*pRgn*<br/>
Identifica una región.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las dos regiones son equivalentes; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>  CRgn::FromHandle

Devuelve un puntero a un `CRgn` objeto cuando se especifica un identificador a una región de Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parámetros

*hRgn*<br/>
Especifica un identificador de una región de Windows.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CRgn` . Si la función no se realizó correctamente, el valor devuelto es NULL.

### <a name="remarks"></a>Comentarios

Si un `CRgn` objeto no está asociado al identificador, un archivo temporal `CRgn` objeto creado y conectado. Este temporal `CRgn` objeto es válido solo hasta que la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, que hora gráfico temporal todos los objetos se eliminan. Otra forma de expresarlo es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.

##  <a name="getregiondata"></a>  CRgn::GetRegionData

Llena el búfer especificado con la descripción de la región de datos.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parámetros

*lpRgnData*<br/>
Apunta a un [RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-_rgndata) estructura de datos que recibe la información. Si este parámetro es NULL, el valor devuelto contiene el número de bytes necesarios para los datos de la región.

*nCount*<br/>
Especifica el tamaño, en bytes, de la *lpRgnData* búfer.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente y *nCount* especifica un número suficiente de bytes, el valor devuelto es siempre *nCount*. Si se produce un error en la función, o si *nCount* especifica menor que el número adecuado de bytes, el valor devuelto es 0 (error).

### <a name="remarks"></a>Comentarios

Estos datos incluyen las dimensiones de los rectángulos que componen la región. Esta función se utiliza junto con el `CRgn::CreateFromData` función.

##  <a name="getrgnbox"></a>  CRgn::GetRgnBox

Recupera las coordenadas del rectángulo delimitador de la `CRgn` objeto.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un `RECT` estructura o `CRect` objeto para recibir las coordenadas del rectángulo delimitador. El `RECT` estructura tiene el formato siguiente:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Valor devuelto

Especifica el tipo de la región. Puede ser cualquiera de los siguientes valores:

- Región COMPLEXREGION tiene superpuesto en los bordes.

- Región NULLREGION está vacío.

- ERROR `CRgn` el objeto no especifica una región válida.

- Región SIMPLEREGION no tiene bordes superpuestos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreatePolygonRgn](#createpolygonrgn).

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

Mueve la región que se almacenan en la `CRgn` objeto por los desplazamientos especificados.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica el número de unidades para mover a la izquierda o derecha.

*y*<br/>
Especifica el número de unidades que se mueven hacia arriba o hacia abajo.

*punto*<br/>
La coordenada x de *punto* especifica el número de unidades para mover a la izquierda o derecha. La coordenada y de *punto* especifica el número de unidades que se mueven hacia arriba o hacia abajo. El *punto* parámetro puede ser un `POINT` estructura o un `CPoint` objeto.

### <a name="return-value"></a>Valor devuelto

Tipo de la nueva región. Puede ser cualquiera de los siguientes valores:

- Región COMPLEXREGION tiene superpuesto en los bordes.

- Identificador de ERROR la región no es válido.

- Región NULLREGION está vacío.

- Región SIMPLEREGION no tiene bordes superpuestos.

### <a name="remarks"></a>Comentarios

La función mueve a la región *x* unidades a lo largo del eje x y *y* unidades a lo largo del eje y.

Los valores de coordenadas de una región deben ser menor o igual que 32.767 y mayor o igual a -32.768. El *x* y *y* parámetros deben elegir con cuidado para evitar que las coordenadas de la región no válido.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRgn::CreateEllipticRgn](#createellipticrgn).

##  <a name="operator_hrgn"></a>  CRgn::operator HRGN

Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CRgn` objeto.

```
operator HRGN() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, un identificador para el objeto GDI de Windows representado por la `CRgn` objeto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este es un operador de conversión, que admite el uso directo de un objeto HRGN.

Para obtener más información sobre el uso de objetos gráficos, vea el artículo [gráfico de objetos](/windows/desktop/gdi/graphic-objects) en el SDK de Windows.

##  <a name="ptinregion"></a>  CRgn::PtInRegion

Comprueba si el punto especificado por *x* y *y* está en la región que se almacenan en la `CRgn` objeto.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica la coordenada x lógica del punto de prueba.

*y*<br/>
Especifica la coordenada y lógica de punto de prueba.

*punto*<br/>
Las coordenadas x e y de *punto* especificar las coordenadas x e y del punto para probar el valor de. El *punto* parámetro puede ser un `POINT` estructura o un `CPoint` objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto está en la región; en caso contrario, es 0.

##  <a name="rectinregion"></a>  CRgn::RectInRegion

Determina si cualquier parte del rectángulo especificado por *lpRect* está dentro de los límites de la región que se almacenan en la `CRgn` objeto.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un `RECT` estructura o `CRect` objeto. El `RECT` estructura tiene el formato siguiente:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si cualquier parte del rectángulo especificado se encuentra dentro de los límites de la región; en caso contrario, es 0.

##  <a name="setrectrgn"></a>  CRgn::SetRectRgn

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

*X1*<br/>
Especifica la coordenada x de la esquina superior izquierda de la región rectangular.

*y1*<br/>
Especifica la coordenada y de la esquina superior izquierda de la región rectangular.

*X2*<br/>
Especifica la coordenada x de la esquina inferior derecha de la región rectangular.

*y2*<br/>
Especifica la coordenada y de la esquina inferior derecha de la región rectangular.

*lpRect*<br/>
Especifica la región rectangular. Puede ser un puntero a un `RECT` estructura o un `CRect` objeto.

### <a name="remarks"></a>Comentarios

A diferencia de [CreateRectRgn](#createrectrgn), sin embargo, no asigna memoria adicional desde el montón local de aplicación de Windows. En su lugar, usa el espacio asignado para la región se almacena en la `CRgn` objeto. Esto significa que el `CRgn` objeto ya debe haber se ha inicializado con una región de Windows válida antes de llamar a `SetRectRgn`. Los puntos proporcionados por *x1*, *y1*, *x2*, y *y2* especificar el tamaño mínimo de espacio asignado.

Use esta función en lugar de la `CreateRectRgn` la función miembro para evitar llamadas al administrador de memoria local.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

