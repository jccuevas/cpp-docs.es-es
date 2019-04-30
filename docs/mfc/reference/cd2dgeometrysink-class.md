---
title: Clase CD2DGeometrySink
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
ms.openlocfilehash: 48c88f0b837b2e49e4c87f07a9aa28c16a66c1e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391262"
---
# <a name="cd2dgeometrysink-class"></a>Clase CD2DGeometrySink

Un contenedor para ID2D1GeometrySink.

## <a name="syntax"></a>Sintaxis

```
class CD2DGeometrySink;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Construye un objeto CD2DGeometrySink del objeto CD2DPathGeometry.|
|[CD2DGeometrySink::~CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destructor. Se llama cuando se destruye un objeto de receptor de geometría D2D.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Agrega un arco único a la geometría de trayecto|
|[CD2DGeometrySink::AddBezier](#addbezier)|Crea una curva Bézier cúbica entre el punto actual y el punto final especificado.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Crea una secuencia de curvas Bézier cúbicas y las agrega al receptor de geometría.|
|[CD2DGeometrySink::AddLine](#addline)|Crea un segmento de línea entre el punto actual y el punto final especificado y lo agrega al receptor de geometría.|
|[CD2DGeometrySink::AddLines](#addlines)|Crea una secuencia de líneas con los puntos especificados y las agrega al receptor de geometría.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Crea una curva Bézier cuadrática entre el punto actual y el punto final especificado.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Agrega una secuencia de segmentos de Bézier cuadrática como una matriz en una sola llamada.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Inicia una nueva figura en el punto especificado.|
|[CD2DGeometrySink::Close](#close)|Cierra el receptor de geometría|
|[CD2DGeometrySink::EndFigure](#endfigure)|Finaliza la figura actual; Si lo desea, lo cierra.|
|[CD2DGeometrySink::Get](#get)|Interfaz de ID2D1GeometrySink devuelve|
|[CD2DGeometrySink::IsValid](#isvalid)|Comprueba la validez del receptor de geometría|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Especifica el método utilizado para determinar que son puntos dentro de la geometría descrita por este receptor de geometría y que son puntos fuera.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Especifica las opciones de trazo y combinación que se puede aplicar a nuevos segmentos agregados al receptor de geometría.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink*](#operator_id2d1geometrysink_star)|Interfaz de ID2D1GeometrySink devuelve|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Un puntero a un ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CD2DGeometrySink`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="_dtorcd2dgeometrysink"></a>  CD2DGeometrySink::~CD2DGeometrySink

Destructor. Se llama cuando se destruye un objeto de receptor de geometría D2D.

```
virtual ~CD2DGeometrySink();
```

##  <a name="addarc"></a>  CD2DGeometrySink::AddArc

Agrega un arco único a la geometría de trayecto

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Parámetros

*arc*<br/>
Para agregar a la figura el segmento de arco

##  <a name="addbezier"></a>  CD2DGeometrySink::AddBezier

Crea una curva Bézier cúbica entre el punto actual y el punto final especificado.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parámetros

*bezier*<br/>
Una estructura que describe los puntos de control y el punto final de la curva de Bézier para agregar.

##  <a name="addbeziers"></a>  CD2DGeometrySink::AddBeziers

Crea una secuencia de curvas Bézier cúbicas y las agrega al receptor de geometría.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parámetros

*beziers*<br/>
Una matriz de segmentos de Bézier que describe las curvas de Bézier para crear. Se dibuja una curva desde el punto del receptor de la geometría actual (el punto final del último segmento dibujado o la ubicación especificada por a BeginFigure) hasta el punto final del primer segmento de Bézier en la matriz. Si la matriz contiene los segmentos de Bézier adicionales, cada segmento posterior de Bézier usa el punto final del segmento Bézier anterior como punto de inicio.

##  <a name="addline"></a>  CD2DGeometrySink::AddLine

Crea un segmento de línea entre el punto actual y el punto final especificado y lo agrega al receptor de geometría.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
El punto final de la línea que se va a dibujar.

##  <a name="addlines"></a>  CD2DGeometrySink::AddLines

Crea una secuencia de líneas con los puntos especificados y las agrega al receptor de geometría.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Parámetros

*points*<br/>
Una matriz de uno o varios puntos que describen las líneas que se va a dibujar. Se dibuja una línea desde el punto del receptor de la geometría actual (el punto final del último segmento dibujado o la ubicación especificada por a BeginFigure) hasta el primer punto de la matriz. Si la matriz contiene puntos adicionales, se dibuja una línea desde el primer punto hasta el segundo punto de la matriz, desde el punto de segundo para el tercer punto y así sucesivamente. Una matriz de una secuencia de los puntos de conexión de las líneas que se va a dibujar.

##  <a name="addquadraticbezier"></a>  CD2DGeometrySink::AddQuadraticBezier

Crea una curva Bézier cuadrática entre el punto actual y el punto final especificado.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parámetros

*bezier*<br/>
Una estructura que describe el punto de control y el punto final de la curva Bézier cuadrática a agregar.

##  <a name="addquadraticbeziers"></a>  CD2DGeometrySink::AddQuadraticBeziers

Agrega una secuencia de segmentos de Bézier cuadrática como una matriz en una sola llamada.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parámetros

*beziers*<br/>
Una matriz de una secuencia de segmentos de Bézier cuadrática.

##  <a name="beginfigure"></a>  CD2DGeometrySink::BeginFigure

Inicia una nueva figura en el punto especificado.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Parámetros

*startPoint*<br/>
El punto donde se comienzan a la nueva figura.

*figureBegin*<br/>
Si debe ser la nueva figura hueco o rellena.

##  <a name="cd2dgeometrysink"></a>  CD2DGeometrySink::CD2DGeometrySink

Construye un objeto CD2DGeometrySink del objeto CD2DPathGeometry.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Parámetros

*pathGeometry*<br/>
Un objeto CD2DPathGeometry existente.

##  <a name="close"></a>  CD2DGeometrySink::Close

Cierra el receptor de geometría

```
BOOL Close();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; en caso contrario, FALSE.

##  <a name="endfigure"></a>  CD2DGeometrySink::EndFigure

Finaliza la figura actual; Si lo desea, lo cierra.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Parámetros

*figureEnd*<br/>
Un valor que indica si se cierra la figura actual. Si la figura está cerrada, se dibuja una línea entre el punto actual y el punto inicial especificado por a BeginFigure.

##  <a name="get"></a>  CD2DGeometrySink::Get

Interfaz de ID2D1GeometrySink devuelve

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1GeometrySink o NULL si el objeto no se ha inicializado todavía.

##  <a name="isvalid"></a>  CD2DGeometrySink::IsValid

Comprueba la validez del receptor de geometría

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el receptor de geometría es válido; en caso contrario, FALSE.

##  <a name="m_psink"></a>  CD2DGeometrySink::m_pSink

Un puntero a un ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

##  <a name="operator_id2d1geometrysink_star"></a>  CD2DGeometrySink::operator ID2D1GeometrySink*

Interfaz de ID2D1GeometrySink devuelve

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1GeometrySink o NULL si el objeto no se ha inicializado todavía.

##  <a name="setfillmode"></a>  CD2DGeometrySink::SetFillMode

Especifica el método utilizado para determinar que son puntos dentro de la geometría descrita por este receptor de geometría y que son puntos fuera.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Parámetros

*fillMode*<br/>
El método utilizado para determinar si un punto determinado forma parte de la geometría.

##  <a name="setsegmentflags"></a>  CD2DGeometrySink::SetSegmentFlags

Especifica las opciones de trazo y combinación que se puede aplicar a nuevos segmentos agregados al receptor de geometría.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Parámetros

*vertexFlags*<br/>
Opciones de trazo y combinación que se aplicarán a nuevos segmentos que se agregan a la geometría de receptor.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
