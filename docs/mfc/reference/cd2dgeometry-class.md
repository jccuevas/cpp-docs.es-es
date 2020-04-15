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
ms.openlocfilehash: 2631005fcedfb8d5db69667e22c375f585b4f044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369247"
---
# <a name="cd2dgeometry-class"></a>Clase CD2DGeometry

Un contenedor para ID2D1Geometry.

## <a name="syntax"></a>Sintaxis

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Construye un CD2DGeometry objeto.|
|[CD2DGeometry::-CD2DGeometry](#_dtorcd2dgeometry)|Destructor. Se llama cuando se destruye un objeto de geometría D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometry::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Combina esta geometría con la geometría especificada y almacena el resultado en un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Describe la intersección entre esta geometría y la geometría especificada. La comparación se realiza utilizando la tolerancia de aplanamiento especificada.|
|[CD2DGeometry::ComputeArea](#computearea)|Calcula el área de la geometría después de que la matriz especificada la haya transformado y aplanado utilizando la tolerancia especificada.|
|[CD2DGeometry::ComputeLength](#computelength)|Calcula la longitud de la geometría como si cada segmento se hubiera desenrollado en una línea.|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Calcula el punto y el vector tangente a la distancia especificada a lo largo de la geometría después de que la matriz especificada lo haya transformado y aplanado utilizando la tolerancia especificada.|
|[CD2DGeometry::Destroy](#destroy)|Destruye un objeto CD2DGeometry. (Reemplaza [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometry::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Indica si el área rellenada por la geometría contendría el punto especificado dada la tolerancia de aplanamiento especificada.|
|[CD2DGeometry::Get](#get)|Devuelve id2D1Geometry interfaz|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Obtiene los límites de la geometría después de que se ha ampliado por el ancho y el estilo de trazo especificados y transformado por la matriz especificada.|
|[CD2DGeometry::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometry::Outline](#outline)|Calcula el contorno de la geometría y escribe el resultado en un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::Simplificar](#simplify)|Crea una versión simplificada de la geometría que contiene solo líneas y (opcionalmente) curvas Bézier cúbicas y escribe el resultado en un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Determina si el trazo de la geometría contiene el punto especificado dado el grosor de trazo, el estilo y la transformación especificados.|
|[CD2DGeometry::Tessellate](#tessellate)|Crea un conjunto de triángulos hacia la derecha que cubren la geometría después de que se haya transformado mediante la matriz especificada y aplanada mediante la tolerancia especificada.|
|[CD2DGeometry::Widen](#widen)|Amplía la geometría por el trazo especificado y escribe el resultado en un ID2D1SimplifiedGeometrySink después de que se haya transformado por la matriz especificada y acoplado utilizando la tolerancia especificada.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometry::operator ID2D1Geometry*](#operator_id2d1geometry_star)|Devuelve id2D1Geometry interfaz|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Un puntero a un ID2D1Geometry.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a>CD2DGeometry::-CD2DGeometry

Destructor. Se llama cuando se destruye un objeto de geometría D2D.

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a>CD2DGeometry::Attach

Adjunta la interfaz de recursos existente al objeto

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry

Construye un CD2DGeometry objeto.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry

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
La geometría que se combinará con esta instancia.

*combineMode*<br/>
El tipo de operación de combinación que se debe realizar.

*inputGeometryTransform*<br/>
La transformación que se aplicará a inputGeometry antes de combinar.

*geometrySink*<br/>
El resultado de la operación de combinación.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry

Describe la intersección entre esta geometría y la geometría especificada. La comparación se realiza utilizando la tolerancia de aplanamiento especificada.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*inputGeometry*<br/>
La geometría que se va a probar.

*inputGeometryTransform*<br/>
La transformación que se aplicará a inputGeometry.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a>CD2DGeometry::ComputeArea

Calcula el área de la geometría después de que la matriz especificada la haya transformado y aplanado utilizando la tolerancia especificada.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
La transformación que se aplicará a esta geometría antes de calcular su área.

*Área*<br/>
Cuando se devuelve este método, contiene un puntero al área de la versión transformada y aplanada de esta geometría. Debe asignar almacenamiento para este parámetro.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a>CD2DGeometry::ComputeLength

Calcula la longitud de la geometría como si cada segmento se hubiera desenrollado en una línea.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
Transformación que se aplicará a la geometría antes de calcular su longitud.

*length*<br/>
Cuando se devuelve este método, contiene un puntero a la longitud de la geometría. Para geometrías cerradas, la longitud incluye un segmento de cierre implícito. Debe asignar almacenamiento para este parámetro.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength

Calcula el punto y el vector tangente a la distancia especificada a lo largo de la geometría después de que la matriz especificada lo haya transformado y aplanado utilizando la tolerancia especificada.

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
La distancia a lo largo de la geometría del punto y tangente de encontrar. Si esta distancia es menor que 0, este método calcula el primer punto de la geometría. Si esta distancia es mayor que la longitud de la geometría, este método calcula el último punto de la geometría.

*worldTransform*<br/>
Transformación que se aplicará a la geometría antes de calcular el punto y la tangente especificados.

*Punto*<br/>
La ubicación a la distancia especificada a lo largo de la geometría. Si la geometría está vacía, este punto contiene NaN como sus valores x e y.

*unitTangentVector*<br/>
Cuando se devuelve este método, contiene un puntero al vector tangente a la distancia especificada a lo largo de la geometría. Si la geometría está vacía, este vector contiene NaN como sus valores x e y. Debe asignar almacenamiento para este parámetro.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a>CD2DGeometry::Destroy

Destruye un objeto CD2DGeometry.

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a>CD2DGeometry::Detach

Separa la interfaz de recursos del objeto

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint

Indica si el área rellenada por la geometría contendría el punto especificado dada la tolerancia de aplanamiento especificada.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
El punto para realizar la prueba.

*worldTransform*<br/>
Transformación que se aplicará a la geometría antes de realizar pruebas de contención.

*Contiene*<br/>
Cuando se devuelve este método, contiene un valor bool que es TRUE si el área rellenada por la geometría contiene punto; de lo contrario, FALSE. Debe asignar almacenamiento para este parámetro.

*flatteningTolerancia*<br/>
Precisión numérica con la que se calcula la intersección geométrica precisa de la ruta y la trayectoria. Los puntos que faltan en el relleno por menos que la tolerancia todavía se consideran en el interior. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometryget"></a><a name="get"></a>CD2DGeometry::Get

Devuelve id2D1Geometry interfaz

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Geometry o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a>CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
*Límites*

### <a name="return-value"></a>Valor devuelto

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds

Obtiene los límites de la geometría después de que se ha ampliado por el ancho y el estilo de trazo especificados y transformado por la matriz especificada.

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
La cantidad por la que se amplía la geometría acariciando su contorno.

*Strokestyle*<br/>
El estilo del trazo que amplía la geometría.

*worldTransform*<br/>
Transformación que se aplicará a la geometría después de transformar la geometría y después de trazar la geometría.

*Límites*<br/>
Cuando se devuelve este método, contiene los límites de la geometría ampliada. Debe asignar almacenamiento para este parámetro.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a>CD2DGeometry::IsValid

Comprueba la validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el recurso es válido; de lo contrario FALSO.

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry

Un puntero a un ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a>CD2DGeometry::operator ID2D1Geometry*

Devuelve id2D1Geometry interfaz

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Geometry o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dgeometryoutline"></a><a name="outline"></a>CD2DGeometry::Outline

Calcula el contorno de la geometría y escribe el resultado en un ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
Transformación que se aplicará al contorno de geometría.

*geometrySink*<br/>
El ID2D1SimplifiedGeometrySink al que se anexa el contorno transformado de geometría.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a>CD2DGeometry::Simplificar

Crea una versión simplificada de la geometría que contiene solo líneas y (opcionalmente) curvas Bézier cúbicas y escribe el resultado en un ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*simplificaciónOption*<br/>
Valor que especifica si la geometría simplificada debe contener curvas.

*worldTransform*<br/>
Transformación que se aplicará a la geometría simplificada.

*geometrySink*<br/>
El ID2D1SimplifiedGeometrySink al que se anexa la geometría simplificada.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint

Determina si el trazo de la geometría contiene el punto especificado dado el grosor de trazo, el estilo y la transformación especificados.

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

*Punto*<br/>
Punto cuya inclusión se va a comprobar.

*strokeWidth*<br/>
El grosor del trazo que se aplicará.

*Strokestyle*<br/>
El estilo del trazo que se aplicará.

*worldTransform*<br/>
Transformación que se aplicará a la geometría trazada.

*Contiene*<br/>
Cuando se devuelve este método, contiene un valor booleano establecido en TRUE si el trazo de la geometría contiene el punto especificado; de lo contrario, FALSE. Debe asignar almacenamiento para este parámetro.

*flatteningTolerancia*<br/>
Precisión numérica con la que se calcula la intersección geométrica precisa de la ruta y la trayectoria. Los puntos que faltan en el trazo por menos que la tolerancia todavía se consideran en el interior. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a>CD2DGeometry::Tessellate

Crea un conjunto de triángulos hacia la derecha que cubren la geometría después de que se haya transformado mediante la matriz especificada y aplanada mediante la tolerancia especificada.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parámetros

*worldTransform*<br/>
La transformación que se aplicará a esta geometría, o NULL.

*tessellationSink*<br/>
El ID2D1TessellationSink al que se anexa el teselado.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cd2dgeometrywiden"></a><a name="widen"></a>CD2DGeometry::Widen

Amplía la geometría por el trazo especificado y escribe el resultado en un ID2D1SimplifiedGeometrySink después de que se haya transformado por la matriz especificada y acoplado utilizando la tolerancia especificada.

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
La cantidad por la que se amplía la geometría.

*Strokestyle*<br/>
El estilo de trazo que se aplicará a la geometría o NULL.

*worldTransform*<br/>
La transformación que se aplicará a la geometría después de ampliarla.

*geometrySink*<br/>
El ID2D1SimplifiedGeometrySink al que se anexa la geometría ampliada.

*flatteningTolerancia*<br/>
Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores generan resultados más precisos pero hacen que la ejecución sea más lenta.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
