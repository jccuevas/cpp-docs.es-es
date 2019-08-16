---
title: Clase CD2DGeometry
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 4549b2e7981d5f8493ddf9f24477e75a94ddde8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405734"
---
# <a name="cd2dgeometry-class"></a>Clase CD2DGeometry

Un contenedor para ID2D1Geometry.

## <a name="syntax"></a>Sintaxis

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Construye un objeto CD2DGeometry.|
|[CD2DGeometry::~CD2DGeometry](#_dtorcd2dgeometry)|Destructor. Se llama cuando se destruye un objeto de geometría D2D.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometry::Attach](#attach)|Adjunta existente de la interfaz de recurso para el objeto|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Combina esta geometría con la geometría especificada y almacena el resultado en un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Describe la intersección entre esta geometría y la geometría especificada. La comparación se realiza mediante la tolerancia especificada de valores sin formato.|
|[CD2DGeometry::ComputeArea](#computearea)|Calcula el área de la geometría después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.|
|[CD2DGeometry::ComputeLength](#computelength)|Calcula la longitud de la geometría como si estuviera revertido en una línea cada segmento.|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Calcula el vector de punto y tangente a la distancia especificada a lo largo de la geometría después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.|
|[CD2DGeometry::Destroy](#destroy)|Destruye un objeto CD2DGeometry. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometry::Detach](#detach)|Separa la interfaz de recursos desde el objeto|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Indica si el área que rellena la geometría contendría el punto especificado, dado la tolerancia especificada de valores sin formato.|
|[CD2DGeometry::Get](#get)|Interfaz ID2D1Geometry de devoluciones|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Obtiene los límites de la geometría después de haberlo ampliada por el ancho del trazo especificado y el estilo y transforma la matriz especificada.|
|[CD2DGeometry::IsValid](#isvalid)|Comprueba la validez de los recursos (invalidaciones [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometry::Outline](#outline)|Calcula el contorno de la geometría y escribe el resultado en un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::Simplify](#simplify)|Crea una versión simplificada de la geometría que contiene solo líneas y curvas de Bézier cúbicas (opcionalmente) y escribe el resultado en un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Determina si el trazo de la geometría contiene el punto especificado, dado el grosor del trazo especificado, el estilo y la transformación.|
|[CD2DGeometry::Tessellate](#tessellate)|Crea un conjunto de triángulos hacia la derecha que cubren la geometría después de que se haya transformado mediante la matriz especificada y aplanada mediante la tolerancia especificada.|
|[CD2DGeometry::Widen](#widen)|Amplía la geometría con el trazo especificado y escribe el resultado en un ID2D1SimplifiedGeometrySink después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|Interfaz ID2D1Geometry de devoluciones|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Un puntero a un ID2D1Geometry.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="_dtorcd2dgeometry"></a>  CD2DGeometry::~CD2DGeometry

Destructor. Se llama cuando se destruye un objeto de geometría D2D.

```
virtual ~CD2DGeometry();
```

##  <a name="attach"></a>  CD2DGeometry::Attach

Adjunta existente de la interfaz de recurso para el objeto

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry

Construye un objeto CD2DGeometry.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero para el destino de representación.

*bAutoDestroy*<br/>
Indica que se va a destruir el objeto propietario (pParentTarget).

##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry

Combina esta geometría con la geometría especificada y almacena el resultado en un ID2D1SimplifiedGeometrySink.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*inputGeometry*<br/>
Geometría que se va a combinar con esta instancia.

*combineMode*<br/>
El tipo de operación de combinación para realizar.

*inputGeometryTransform*<br/>
Transformación que se aplican a inputGeometry antes de la combinación.

*geometrySink*<br/>
El resultado de la operación de combinación.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry

Describe la intersección entre esta geometría y la geometría especificada. La comparación se realiza mediante la tolerancia especificada de valores sin formato.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*inputGeometry*<br/>
Para probar la geometría.

*inputGeometryTransform*<br/>
Transformación que se aplican a inputGeometry.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="computearea"></a>  CD2DGeometry::ComputeArea

Calcula el área de la geometría después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
Transformación que se aplican a esta geometría antes de calcular su área.

*area*<br/>
Cuando este método finaliza, contiene un puntero al área de la versión transformada y sin estructura jerárquica de esta geometría. Debe asignar el almacenamiento para este parámetro.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="computelength"></a>  CD2DGeometry::ComputeLength

Calcula la longitud de la geometría como si estuviera revertido en una línea cada segmento.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
La transformación para aplicar a la geometría antes de calcular su longitud.

*length*<br/>
Cuando este método finaliza, contiene un puntero a la longitud de la geometría. Para las geometrías cerradas, la longitud incluye un segmento de cierre implícita. Debe asignar el almacenamiento para este parámetro.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength

Calcula el vector de punto y tangente a la distancia especificada a lo largo de la geometría después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*length*<br/>
La distancia a lo largo de la geometría del punto y tangente a buscar. Si la distancia es menor, a continuación, 0, este método calcula el primer punto de la geometría. Si la distancia es mayor que la longitud de la geometría, este método calcula el último punto de la geometría.

*worldTransform*<br/>
La transformación para aplicar a la geometría antes de calcular el punto especificado y la tangente.

*point*<br/>
La ubicación a la distancia a lo largo de la geometría especificada. Si la geometría está vacía, este punto contiene NaN como su x e y valores.

*unitTangentVector*<br/>
Cuando este método finaliza, contiene un puntero al vector tangente a la distancia a lo largo de la geometría especificada. Si la geometría está vacía, este vector contiene NaN como su x e y valores. Debe asignar el almacenamiento para este parámetro.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="destroy"></a>  CD2DGeometry::Destroy

Destruye un objeto CD2DGeometry.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DGeometry::Detach

Separa la interfaz de recursos desde el objeto

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz separada del recurso.

##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint

Indica si el área que rellena la geometría contendría el punto especificado, dado la tolerancia especificada de valores sin formato.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*point*<br/>
El punto de prueba.

*worldTransform*<br/>
La transformación para aplicar a la geometría antes de la prueba de contención.

*contains*<br/>
Cuando este método finaliza, contiene un valor booleano que es TRUE si el área que rellena la geometría contiene el punto; en caso contrario, FALSE. Debe asignar el almacenamiento para este parámetro.

*flatteningTolerance*<br/>
La precisión numérica con la que el trazado geométrico precisa y la intersección de la ruta de acceso se calcula. Falta el relleno a menos que la tolerancia de puntos todavía se consideran dentro. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="get"></a>  CD2DGeometry::Get

Interfaz ID2D1Geometry de devoluciones

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Geometry o NULL si el objeto no se ha inicializado todavía.

##  <a name="getbounds"></a>  CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
*bounds*

### <a name="return-value"></a>Valor devuelto

##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds

Obtiene los límites de la geometría después de haberlo ampliada por el ancho del trazo especificado y el estilo y transforma la matriz especificada.

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*strokeWidth*<br/>
Cantidad por la que se va a ampliar la geometría por trazado su contorno.

*strokeStyle*<br/>
El estilo del trazo que se amplía la geometría.

*worldTransform*<br/>
Una transformación para aplicar a la geometría después de la geometría se transforma y geometría ha sido trazada.

*bounds*<br/>
Cuando este método finaliza, contiene los límites de la geometría ampliada. Debe asignar el almacenamiento para este parámetro.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="isvalid"></a>  CD2DGeometry::IsValid

Comprobaciones de validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el recurso es válida; en caso contrario, FALSE.

##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry

Un puntero a un ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::operator ID2D1Geometry *

Interfaz ID2D1Geometry de devoluciones

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Geometry o NULL si el objeto no se ha inicializado todavía.

##  <a name="outline"></a>  CD2DGeometry::Outline

Calcula el contorno de la geometría y escribe el resultado en un ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
La transformación para aplicar al contorno de geometría.

*geometrySink*<br/>
El ID2D1SimplifiedGeometrySink a la que se anexa el contorno de geometría transformada.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="simplify"></a>  CD2DGeometry::Simplify

Crea una versión simplificada de la geometría que contiene solo líneas y curvas de Bézier cúbicas (opcionalmente) y escribe el resultado en un ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*simplificationOption*<br/>
Un valor que especifica si la geometría simplificada debe contener curvas.

*worldTransform*<br/>
La transformación para aplicar a la geometría simplificada.

*geometrySink*<br/>
El ID2D1SimplifiedGeometrySink a la que se anexa la geometría simplificada.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint

Determina si el trazo de la geometría contiene el punto especificado, dado el grosor del trazo especificado, el estilo y la transformación.

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*point*<br/>
El punto de contención que se buscará.

*strokeWidth*<br/>
El grosor del trazo que se va a aplicar.

*strokeStyle*<br/>
El estilo del trazo que se va a aplicar.

*worldTransform*<br/>
La transformación para aplicar a la geometría trazar el objeto.

*contains*<br/>
Cuando este método finaliza, contiene un valor booleano establecido en TRUE si el trazo de la geometría contiene el punto especificado; en caso contrario, FALSE. Debe asignar el almacenamiento para este parámetro.

*flatteningTolerance*<br/>
La precisión numérica con la que el trazado geométrico precisa y la intersección de la ruta de acceso se calcula. Falta el trazo en menos de la tolerancia de puntos todavía se consideran dentro. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="tessellate"></a>  CD2DGeometry::Tessellate

Crea un conjunto de triángulos hacia la derecha que cubren la geometría después de que se haya transformado mediante la matriz especificada y aplanada mediante la tolerancia especificada.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
Transformación que se aplican a esta geometría, o NULL.

*tessellationSink*<br/>
El ID2D1TessellationSink a la que se anexan el divididas en mosaicos.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="widen"></a>  CD2DGeometry::Widen

Amplía la geometría con el trazo especificado y escribe el resultado en un ID2D1SimplifiedGeometrySink después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*strokeWidth*<br/>
Cantidad por la que se va a ampliar la geometría.

*strokeStyle*<br/>
Estilo del trazo que se aplicará a la geometría, o NULL.

*worldTransform*<br/>
La transformación para aplicar a la geometría después de la ampliación de él.

*geometrySink*<br/>
El ID2D1SimplifiedGeometrySink a la que se anexa la geometría ampliada.

*flatteningTolerance*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
