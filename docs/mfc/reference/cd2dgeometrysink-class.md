---
title: Clase CD2DGeometrySink | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink class
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8a51d9475437ae460340d419a88bc46effa81f5f
ms.lasthandoff: 02/24/2017

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
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Construye un objeto CD2DGeometrySink del objeto CD2DPathGeometry.|  
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destructor. Se llama cuando se destruye un objeto de receptor de geometría D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|Agrega un arco único a la geometría de trayecto|  
|[CD2DGeometrySink::AddBezier](#addbezier)|Crea una curva Bézier cúbica entre el punto actual y el extremo especificado.|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Crea una secuencia de curvas Bézier cúbicas y los agrega al receptor de geometría.|  
|[CD2DGeometrySink::AddLine](#addline)|Crea un segmento de línea entre el punto actual y el extremo especificado y lo agrega al receptor de geometría.|  
|[CD2DGeometrySink::AddLines](#addlines)|Crea una secuencia de líneas con los puntos especificados y los agrega al receptor de geometría.|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Crea una curva Bézier cuadrática entre el punto actual y el extremo especificado.|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Agrega una secuencia de segmentos de Bézier cuadrática como una matriz en una sola llamada.|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Inicia una nueva figura en el punto especificado.|  
|[CD2DGeometrySink::Close](#close)|Cierra el receptor de geometría|  
|[CD2DGeometrySink::EndFigure](#endfigure)|Finaliza la figura actual; Opcionalmente, lo cierra.|  
|[CD2DGeometrySink::Get](#get)|Interfaz de ID2D1GeometrySink devuelve|  
|[CD2DGeometrySink::IsValid](#isvalid)|Comprueba la validez del receptor de geometría|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Especifica el método utilizado para determinar qué puntos están dentro de la geometría descrita por este receptor de geometría y que son puntos fuera.|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Especifica las opciones de trazo y combinación que se aplicará a nuevos segmentos agregados al receptor de geometría.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Interfaz de ID2D1GeometrySink devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DGeometrySink::m_pSink](#m_psink)|Puntero a un ID2D1GeometrySink.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CD2DGeometrySink`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink:: ~ CD2DGeometrySink  
 Destructor. Se llama cuando se destruye un objeto de receptor de geometría D2D.  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="addarc"></a>CD2DGeometrySink::AddArc  
 Agrega un arco único a la geometría de trayecto  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>Parámetros  
 `arc`  
 El segmento de arco para agregar a la ilustración  
  
##  <a name="addbezier"></a>CD2DGeometrySink::AddBezier  
 Crea una curva Bézier cúbica entre el punto actual y el extremo especificado.  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Parámetros  
 `bezier`  
 Una estructura que describe los puntos de control y el punto final de la curva de Bézier para agregar.  
  
##  <a name="addbeziers"></a>CD2DGeometrySink::AddBeziers  
 Crea una secuencia de curvas Bézier cúbicas y los agrega al receptor de geometría.  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Parámetros  
 `beziers`  
 Una matriz de los segmentos de curva que describe las curvas de Bézier para crear. Se dibuja una curva desde el punto actual del receptor de la geometría (el punto final del último segmento dibuja o la ubicación especificada por a BeginFigure) hasta el punto final del primer segmento de Bézier en la matriz. Si la matriz contiene los segmentos de curva adicionales, cada segmento de Bézier posterior usa el punto final del segmento de Bézier anterior como punto de inicio.  
  
##  <a name="addline"></a>CD2DGeometrySink::AddLine  
 Crea un segmento de línea entre el punto actual y el extremo especificado y lo agrega al receptor de geometría.  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 El punto final de la línea para dibujar.  
  
##  <a name="addlines"></a>CD2DGeometrySink::AddLines  
 Crea una secuencia de líneas con los puntos especificados y los agrega al receptor de geometría.  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>Parámetros  
 `points`  
 Una matriz de uno o varios puntos que describen las líneas para dibujar. Se dibuja una línea desde el punto actual del receptor de la geometría (el punto final del último segmento dibuja o la ubicación especificada por a BeginFigure) hasta el primer punto de la matriz. Si la matriz contiene puntos adicionales, se dibuja una línea desde el primer punto hasta el segundo punto de la matriz desde el segundo punto para el tercer punto y así sucesivamente. Una matriz de una secuencia de los puntos finales de las líneas para dibujar.  
  
##  <a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier  
 Crea una curva Bézier cuadrática entre el punto actual y el extremo especificado.  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Parámetros  
 `bezier`  
 Una estructura que describe el punto de control y el punto final de la curva de Bézier cuadrática a agregar.  
  
##  <a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers  
 Agrega una secuencia de segmentos de Bézier cuadrática como una matriz en una sola llamada.  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Parámetros  
 `beziers`  
 Una matriz de una secuencia de segmentos de Bézier cuadrática.  
  
##  <a name="beginfigure"></a>CD2DGeometrySink::BeginFigure  
 Inicia una nueva figura en el punto especificado.  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>Parámetros  
 `startPoint`  
 El punto donde debe comenzar la nueva figura.  
  
 `figureBegin`  
 Si la nueva figura debería tener vacío o relleno.  
  
##  <a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink  
 Construye un objeto CD2DGeometrySink del objeto CD2DPathGeometry.  
  
```  
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```  
  
### <a name="parameters"></a>Parámetros  
 `pathGeometry`  
 Un objeto CD2DPathGeometry existente.  
  
##  <a name="close"></a>CD2DGeometrySink::Close  
 Cierra el receptor de geometría  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, FALSE.  
  
##  <a name="endfigure"></a>CD2DGeometrySink::EndFigure  
 Finaliza la figura actual; Opcionalmente, lo cierra.  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `figureEnd`  
 Un valor que indica si se cierra la figura actual. Si la figura está cerrada, se dibuja una línea entre el punto actual y el punto de inicio especificado por a BeginFigure.  
  
##  <a name="get"></a>CD2DGeometrySink::Get  
 Interfaz de ID2D1GeometrySink devuelve  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1GeometrySink o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="isvalid"></a>CD2DGeometrySink::IsValid  
 Comprueba la validez del receptor de geometría  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el receptor de geometry es válido; de lo contrario, FALSE.  
  
##  <a name="m_psink"></a>CD2DGeometrySink::m_pSink  
 Puntero a un ID2D1GeometrySink.  
  
```  
ID2D1GeometrySink* m_pSink;  
```  
  
##  <a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink *  
 Interfaz de ID2D1GeometrySink devuelve  
  
```  
operator ID2D1GeometrySink*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1GeometrySink o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="setfillmode"></a>CD2DGeometrySink::SetFillMode  
 Especifica el método utilizado para determinar qué puntos están dentro de la geometría descrita por este receptor de geometría y que son puntos fuera.  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `fillMode`  
 El método utilizado para determinar si un punto determinado forma parte de la geometría.  
  
##  <a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags  
 Especifica las opciones de trazo y combinación que se aplicará a nuevos segmentos agregados al receptor de geometría.  
  
```  
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `vertexFlags`  
 Opciones de trazos y combinación que se aplicará a nuevos segmentos agregados al receptor de geometría.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

