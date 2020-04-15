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
ms.openlocfilehash: cb51c7b11f75debece61105bf20a201b6eab80a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369239"
---
# <a name="cd2dgeometrysink-class"></a>Clase CD2DGeometrySink

Un contenedor para ID2D1GeometrySink.

## <a name="syntax"></a>Sintaxis

```
class CD2DGeometrySink;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Construye un objeto CD2DGeometrySink a partir del objeto CD2DPathGeometry.|
|[CD2DGeometrySink::-CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destructor. Se llama cuando se destruye un objeto de receptor de geometría D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Añade un único arco a la geometría del trazado|
|[CD2DGeometrySink::AddBezier](#addbezier)|Crea una curva Bézier cúbica entre el punto actual y el punto final especificado.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Crea una secuencia de curvas Bézier cúbicas y las agrega al sumidero de geometría.|
|[CD2DGeometrySink::AddLine](#addline)|Crea un segmento de línea entre el punto actual y el punto final especificado y lo agrega al sumidero de geometría.|
|[CD2DGeometrySink::AddLines](#addlines)|Crea una secuencia de líneas utilizando los puntos especificados y las agrega al receptor de geometría.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Crea una curva Bézier cuadrática entre el punto actual y el punto final especificado.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Agrega una secuencia de segmentos Bézier cuadráticos como una matriz en una sola llamada.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Inicia una nueva figura en el punto especificado.|
|[CD2DGeometrySink::Cerrar](#close)|Cierra el sumidero de geometría|
|[CD2DGeometrySink::EndFigure](#endfigure)|Finaliza la figura actual; opcionalmente, lo cierra.|
|[CD2DGeometrySink::Get](#get)|Devuelve id2D1GeometrySink interfaz|
|[CD2DGeometrySink::IsValid](#isvalid)|Comprueba la validez del sumidero de geometría|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Especifica el método utilizado para determinar qué puntos están dentro de la geometría descrita por este sumidero de geometría y qué puntos están fuera.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Especifica las opciones de trazo y unión que se aplicarán a los nuevos segmentos agregados al receptor de geometría.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink*](#operator_id2d1geometrysink_star)|Devuelve id2D1GeometrySink interfaz|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Un puntero a un ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CD2DGeometrySink`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink::-CD2DGeometrySink

Destructor. Se llama cuando se destruye un objeto de receptor de geometría D2D.

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2DGeometrySink::AddArc

Añade un único arco a la geometría del trazado

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Parámetros

*Arco*<br/>
El segmento de arco que se va a añadir a la figura

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2DGeometrySink::AddBezier

Crea una curva Bézier cúbica entre el punto actual y el punto final especificado.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parámetros

*Bezier*<br/>
Estructura que describe los puntos de control y el punto final de la curva Bézier que se va a agregar.

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2DGeometrySink::AddBeziers

Crea una secuencia de curvas Bézier cúbicas y las agrega al sumidero de geometría.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parámetros

*Beziers*<br/>
Matriz de segmentos de Bézier que describe las curvas de Bézier que se van a crear. Una curva se dibuja desde el punto actual del receptor de geometría (el punto final del último segmento dibujado o la ubicación especificada por BeginFigure) hasta el punto final del primer segmento Dezier de la matriz. si la matriz contiene segmentos Bézier adicionales, cada segmento Dezier posterior utiliza el punto final del segmento Bézier anterior como punto inicial.

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2DGeometrySink::AddLine

Crea un segmento de línea entre el punto actual y el punto final especificado y lo agrega al sumidero de geometría.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
El punto final de la línea que se desea dibujar.

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2DGeometrySink::AddLines

Crea una secuencia de líneas utilizando los puntos especificados y las agrega al receptor de geometría.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Parámetros

*Puntos*<br/>
Matriz de uno o más puntos que describen las líneas que se deben dibujar. Una línea se dibuja desde el punto actual del receptor de geometría (el punto final del último segmento dibujado o la ubicación especificada por BeginFigure) hasta el primer punto de la matriz. si la matriz contiene puntos adicionales, se dibuja una línea desde el primer punto hasta el segundo punto de la matriz, desde el segundo punto hasta el tercer punto, y así sucesivamente. Matriz de una secuencia de los puntos finales de las líneas que se han de dibujar.

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier

Crea una curva Bézier cuadrática entre el punto actual y el punto final especificado.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parámetros

*Bezier*<br/>
Estructura que describe el punto de control y el punto final de la curva Bézier cuadrática que se va a agregar.

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers

Agrega una secuencia de segmentos Bézier cuadráticos como una matriz en una sola llamada.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parámetros

*Beziers*<br/>
Una matriz de una secuencia de segmentos Bézier cuadráticos.

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2DGeometrySink::BeginFigure

Inicia una nueva figura en el punto especificado.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Parámetros

*startPoint*<br/>
El punto en el que comenzar la nueva figura.

*figuraComenzar*<br/>
Si la nueva figura debe estar hueca o llena.

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink

Construye un objeto CD2DGeometrySink a partir del objeto CD2DPathGeometry.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Parámetros

*pathGeometry*<br/>
Un objeto CD2DPathGeometry existente.

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a>CD2DGeometrySink::Cerrar

Cierra el sumidero de geometría

```
BOOL Close();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario FALSO.

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2DGeometrySink::EndFigure

Finaliza la figura actual; opcionalmente, lo cierra.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Parámetros

*figureEnd*<br/>
Valor que indica si la figura actual está cerrada. Si la figura está cerrada, se dibuja una línea entre el punto actual y el punto inicial especificado por BeginFigure.

## <a name="cd2dgeometrysinkget"></a><a name="get"></a>CD2DGeometrySink::Get

Devuelve id2D1GeometrySink interfaz

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1GeometrySink o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2DGeometrySink::IsValid

Comprueba la validez del sumidero de geometría

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el receptor de geometría es válido; de lo contrario FALSO.

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a>CD2DGeometrySink::m_pSink

Un puntero a un ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink*

Devuelve id2D1GeometrySink interfaz

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1GeometrySink o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2DGeometrySink::SetFillMode

Especifica el método utilizado para determinar qué puntos están dentro de la geometría descrita por este sumidero de geometría y qué puntos están fuera.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Parámetros

*fillMode*<br/>
Método utilizado para determinar si un punto determinado forma parte de la geometría.

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags

Especifica las opciones de trazo y unión que se aplicarán a los nuevos segmentos agregados al receptor de geometría.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Parámetros

*vertexFlags*<br/>
Las opciones de trazo y unión se aplicarán a los nuevos segmentos añadidos al sumidero de geometría.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
