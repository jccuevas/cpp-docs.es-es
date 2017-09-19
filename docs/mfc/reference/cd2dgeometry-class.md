---
title: Clase CD2DGeometry | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometry class
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 948b2e2154259557e3a52c2045586cffce2a16f8
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Construye un objeto CD2DGeometry.|  
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|Destructor. Se llama cuando se destruye un objeto geometry de D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DGeometry::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Combina esta geometría con la geometría especificada y almacena el resultado en un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Describe la intersección entre esta geometría y la geometría especificada. La comparación se realiza mediante la tolerancia de acoplamiento especificada.|  
|[CD2DGeometry::ComputeArea](#computearea)|Calcula el área de la geometría después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.|  
|[CD2DGeometry::ComputeLength](#computelength)|Calcula la longitud de la geometría como si estuviera revertido en una línea de cada segmento.|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Calcula el vector de punto y tangente a la distancia especificada a lo largo de la geometría después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.|  
|[CD2DGeometry::Destroy](#destroy)|Destruye un objeto CD2DGeometry. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DGeometry::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Indica si el área que rellena la geometría contiene el punto especificado, dado el acoplamiento tolerancia especificada.|  
|[CD2DGeometry::Get](#get)|Interfaz ID2D1Geometry de devoluciones|  
|[CD2DGeometry::getBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Obtiene los límites de la geometría después de que se ha ampliado por el ancho del trazo especificado y el estilo y se transforma por la matriz especificada.|  
|[CD2DGeometry::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DGeometry::Outline](#outline)|Calcula el contorno de geometry y escribe el resultado en un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::Simplify](#simplify)|Crea una versión simplificada de la geometría que contiene solo líneas y curvas Bézier cúbicas (opcionalmente) y escribe el resultado en un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Determina si el trazo de la geometría contiene el punto especificado, dado el grosor del trazo especificado, el estilo y la transformación.|  
|[CD2DGeometry::Tessellate](#tessellate)|Crea un conjunto de triángulos hacia la derecha que cubren la geometría después de que se haya transformado mediante la matriz especificada y aplanada mediante la tolerancia especificada.|  
|[CD2DGeometry::Widen](#widen)|Amplía la geometría con el trazo especificado y escribe el resultado en un ID2D1SimplifiedGeometrySink después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|Interfaz ID2D1Geometry de devoluciones|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Puntero a un ID2D1Geometry.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DGeometry`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometry"></a>CD2DGeometry:: ~ CD2DGeometry  
 Destructor. Se llama cuando se destruye un objeto geometry de D2D.  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>CD2DGeometry::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry  
 Construye un objeto CD2DGeometry.  
  
```  
CD2DGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry  
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
 `inputGeometry`  
 Geometría que se va a combinar con esta instancia.  
  
 `combineMode`  
 El tipo de operación de combinación para realizar.  
  
 `inputGeometryTransform`  
 Transformación que se aplica a inputGeometry antes de la combinación.  
  
 `geometrySink`  
 El resultado de la operación de combinación.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry  
 Describe la intersección entre esta geometría y la geometría especificada. La comparación se realiza mediante la tolerancia de acoplamiento especificada.  
  
```  
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `inputGeometry`  
 Geometría que se va a probar.  
  
 `inputGeometryTransform`  
 Transformación que se aplica a inputGeometry.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="computearea"></a>CD2DGeometry::ComputeArea  
 Calcula el área de la geometría después de haber sido transformados por la matriz especificada y aplanada mediante la tolerancia especificada.  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `worldTransform`  
 Transformación que se aplican a esta geometría antes de calcular su área.  
  
 `area`  
 Cuando este método finaliza, contiene un puntero para el área de la versión transformado, plana de esta geometría. Debe asignar el almacenamiento para este parámetro.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="computelength"></a>CD2DGeometry::ComputeLength  
 Calcula la longitud de la geometría como si estuviera revertido en una línea de cada segmento.  
  
```  
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& length,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `worldTransform`  
 La transformación que se aplica a la geometría antes de calcular su longitud.  
  
 `length`  
 Cuando este método finaliza, contiene un puntero a la longitud de la geometría. Para las geometrías cerradas, la longitud incluye un segmento de cierre implícita. Debe asignar el almacenamiento para este parámetro.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength  
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
 `length`  
 La distancia a lo largo de la geometría del punto y tangente a buscar. Si la distancia es menos luego 0, este método calcula el primer punto de la geometría. Si la distancia es mayor que la longitud de la geometría, este método calcula el último punto de la geometría.  
  
 `worldTransform`  
 Transformación que se va a aplicar a la geometría antes de calcular el punto especificado y la tangente.  
  
 `point`  
 La ubicación a la distancia especificada a lo largo de la geometría. Si la geometría está vacía, este punto contiene NaN como su x e y valores.  
  
 `unitTangentVector`  
 Cuando este método finaliza, contiene un puntero al vector tangente a la distancia especificada a lo largo de la geometría. Si la geometría está vacía, este vector contiene NaN como su x e y valores. Debe asignar el almacenamiento para este parámetro.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="destroy"></a>CD2DGeometry::Destroy  
 Destruye un objeto CD2DGeometry.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DGeometry::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint  
 Indica si el área que rellena la geometría contiene el punto especificado, dado el acoplamiento tolerancia especificada.  
  
```  
BOOL FillContainsPoint(
    CD2DPointF point,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 El punto de prueba.  
  
 `worldTransform`  
 Transformación que se aplica a la geometría antes de la prueba de contención.  
  
 `contains`  
 Cuando este método finaliza, contiene un valor booleano que es TRUE si el área que rellena la geometría contiene el punto; de lo contrario, FALSE. Debe asignar el almacenamiento para este parámetro.  
  
 `flatteningTolerance`  
 La precisión numérica con la que el trazado geométrico precisa y la intersección de la ruta de acceso se calcula. Falta el relleno inferior a la tolerancia de puntos todavía se consideran dentro. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="get"></a>CD2DGeometry::Get  
 Interfaz ID2D1Geometry de devoluciones  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1Geometry o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="getbounds"></a>CD2DGeometry::getBounds  
  
```   
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,  
CD2DRectF& bounds) const; 
```  
  
### <a name="parameters"></a>Parámetros  
 `worldTransform`  
 `bounds`  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds  
 Obtiene los límites de la geometría después de que se ha ampliado por el ancho del trazo especificado y el estilo y se transforma por la matriz especificada.  
  
```  
BOOL GetWidenedBounds(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DRectF& bounds,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `strokeWidth`  
 Cantidad por la que se va a ampliar la geometría por trazado su esquema.  
  
 `strokeStyle`  
 El estilo del trazo que se amplía la geometría.  
  
 `worldTransform`  
 Una transformación para aplicar a la geometría después de que se transforma la geometría y la geometría ha sido trazada.  
  
 `bounds`  
 Cuando este método vuelve, contiene los límites de la geometría ampliado. Debe asignar el almacenamiento para este parámetro.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de las geometrías. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="isvalid"></a>CD2DGeometry::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válido; de lo contrario, FALSE.  
  
##  <a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry  
 Puntero a un ID2D1Geometry.  
  
```  
ID2D1Geometry* m_pGeometry;  
```  
  
##  <a name="operator_id2d1geometry_star"></a>CD2DGeometry::operator ID2D1Geometry *  
 Interfaz ID2D1Geometry de devoluciones  
  
```  
operator ID2D1Geometry*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1Geometry o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="outline"></a>CD2DGeometry::Outline  
 Calcula el contorno de geometry y escribe el resultado en un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `worldTransform`  
 Transformación que se aplicará al contorno de geometry.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink a la que se anexa el contorno de geometry transformado.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="simplify"></a>CD2DGeometry::Simplify  
 Crea una versión simplificada de la geometría que contiene solo líneas y curvas Bézier cúbicas (opcionalmente) y escribe el resultado en un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `simplificationOption`  
 Un valor que especifica si la geometría simplificada debería contener curvas.  
  
 `worldTransform`  
 Transformación que se aplica a la geometría simplificada.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink a la que se anexa la geometría simplificada.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint  
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
 `point`  
 El punto para comprobar la contención.  
  
 `strokeWidth`  
 El grosor del trazo para aplicar.  
  
 `strokeStyle`  
 El estilo del trazo para aplicar.  
  
 `worldTransform`  
 Transformación que se aplica a la geometría trazada.  
  
 `contains`  
 Cuando este método finaliza, contiene un valor booleano que se establece en TRUE si el trazo de la geometría contiene el punto especificado; de lo contrario, FALSE. Debe asignar el almacenamiento para este parámetro.  
  
 `flatteningTolerance`  
 La precisión numérica con la que el trazado geométrico precisa y la intersección de la ruta de acceso se calcula. Falta el trazo en menos de la tolerancia de puntos todavía se consideran dentro. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="tessellate"></a>CD2DGeometry::Tessellate  
 Crea un conjunto de triángulos hacia la derecha que cubren la geometría después de que se haya transformado mediante la matriz especificada y aplanada mediante la tolerancia especificada.  
  
```  
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1TessellationSink* tessellationSink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `worldTransform`  
 Transformación que se aplica a este objeto geometry o NULL.  
  
 `tessellationSink`  
 ID2D1TessellationSink a la que se anexa el mosaico.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="widen"></a>CD2DGeometry::Widen  
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
 `strokeWidth`  
 Cantidad por la que se va a ampliar la geometría.  
  
 `strokeStyle`  
 El estilo de trazo para aplicar a la geometría o NULL.  
  
 `worldTransform`  
 La transformación que se aplicará a la geometría después de ampliación.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink a la que se anexa la geometría ampliada.  
  
 `flatteningTolerance`  
 Límites máximos de la distancia entre puntos en la aproximación poligonal de la geometría. Los valores menores producen resultados más precisos, pero provocar una ejecución más lenta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

