---
title: CRBMultiMap Clase
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 1e36bc267b3a539d2d1d4bf370b9cdc33828c760
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331420"
---
# <a name="crbmultimap-class"></a>CRBMultiMap Clase

Esta clase representa una estructura de asignación que permite que cada clave se pueda asociar a más de un valor, mediante un árbol binario rojo-negro.

## <a name="syntax"></a>Sintaxis

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>Parámetros

*K*<br/>
El tipo de elemento clave.

*Ⅴ*<br/>
El tipo de elemento value.

*KTraits*<br/>
El código utilizado para copiar o mover elementos clave. Consulte [CElementTraits (Clase)](../../atl/reference/celementtraits-class.md) para obtener más detalles.

*VTraits*<br/>
El código utilizado para copiar o mover elementos de valor.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|El constructor.|
|[CRBMultiMap::-CRBMultiMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Llame a este método para buscar la posición del primer elemento con una clave determinada.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Llame a este método para obtener el valor asociado a una clave determinada y actualizar el valor de posición.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Llame a este método para obtener el elemento asociado a una clave determinada y actualizar el valor de posición.|
|[CRBMultiMap::Insertar](#insert)|Llame a este método para insertar un par de elementos en el mapa.|
|[CRBMultiMap::RemoveKey](#removekey)|Llame a este método para quitar todos los elementos clave/valor de una clave determinada.|

## <a name="remarks"></a>Observaciones

`CRBMultiMap`proporciona compatibilidad con una matriz de asignación de cualquier tipo determinado, administrando una matriz ordenada de elementos y valores clave. A diferencia de la [CRBMap](../../atl/reference/crbmap-class.md) clase, cada clave se puede asociar a más de un valor.

Los elementos (que constan de una clave y un valor) se almacenan en una estructura de árbol binario, mediante el método [CRBMultiMap::Insert.](#insert) Los elementos se pueden quitar mediante el [CRBMultiMap::RemoveKey](#removekey) método, que elimina todos los elementos que coinciden con la clave dada.

El recorrido del árbol es posible con métodos como [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)y [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Es posible que se pueda tener acceso a los valores potencialmente múltiples por clave mediante los métodos [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)y [CRBMultiMap::GetNextWithKey](#getnextwithkey) . Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap) para obtener una ilustración de esto en la práctica.

Los *parámetros KTraits* y *VTraits* son clases de rasgos que contienen cualquier código suplementario necesario para copiar o mover elementos.

`CRBMultiMap`se deriva de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario utilizando el algoritmo Rojo-Negro. Una alternativa `CRBMultiMap` `CRBMap` y es ofrecida por la [clase CAtlMap.](../../atl/reference/catlmap-class.md) Cuando solo es necesario almacenar un pequeño número de elementos, considere la posibilidad de usar la [clase CSimpleMap](../../atl/reference/csimplemap-class.md) en su lugar.

Para obtener una explicación más completa de las distintas clases de colección y sus características y características de rendimiento, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a>CRBMultiMap::CRBMultiMap

El constructor.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Tamaño de bloque.

### <a name="remarks"></a>Observaciones

El *nBlockSize* parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos. El valor predeterminado asignará espacio para 10 elementos a la vez.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a>CRBMultiMap::-CRBMultiMap

Destructor.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a>CRBMultiMap::FindFirstWithKey

Llame a este método para buscar la posición del primer elemento con una clave determinada.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave que identifica el elemento que se va a encontrar.

### <a name="return-value"></a>Valor devuelto

Devuelve la POSITION del primer elemento clave/valor si se encuentra la clave, NULL en caso contrario.

### <a name="remarks"></a>Observaciones

Una clave `CRBMultiMap` en el puede tener uno o más valores asociados. Este método proporcionará el valor de posición del primer valor (que puede, de hecho, ser el único valor) asociado a esa clave en particular. El valor de posición devuelto se puede utilizar con [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) o [CRBMultiMap::GetNextWithKey](#getnextwithkey) para obtener el valor y actualizar la posición.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a>CRBMultiMap::GetNextValueWithKey

Llame a este método para obtener el valor asociado a una clave determinada y actualizar el valor de posición.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor de posición, obtenido con una llamada a [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) o [CRBMultiMap::GetNextWithKey](#getnextwithkey), o una llamada anterior a `GetNextValueWithKey`.

*key*<br/>
Especifica la clave que identifica el elemento que se va a encontrar.

### <a name="return-value"></a>Valor devuelto

Devuelve el par de elementos asociado a la clave dada.

### <a name="remarks"></a>Observaciones

El valor de posición se actualiza para que apunte al siguiente valor asociado a la clave. Si no existen más valores, el valor de posición se establece en NULL.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a>CRBMultiMap::GetNextWithKey

Llame a este método para obtener el elemento asociado a una clave determinada y actualizar el valor de posición.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor de posición, obtenido con una llamada a [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) o [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), o una llamada anterior a `GetNextWithKey`.

*key*<br/>
Especifica la clave que identifica el elemento que se va a encontrar.

### <a name="return-value"></a>Valor devuelto

Devuelve el siguiente elemento [CRBTree::CPair Class](crbtree-class.md#cpair_class) asociado a la clave dada.

### <a name="remarks"></a>Observaciones

El valor de posición se actualiza para que apunte al siguiente valor asociado a la clave. Si no existen más valores, el valor de posición se establece en NULL.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

## <a name="crbmultimapinsert"></a><a name="insert"></a>CRBMultiMap::Insertar

Llame a este método para insertar un par de elementos en el mapa.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
El valor de clave `CRBMultiMap` que se va a agregar al objeto.

*value*<br/>
Valor que se `CRBMultiMap` va a agregar al objeto, asociado a *key*.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del par clave/valor del elemento en el `CRBMultiMap` objeto.

### <a name="remarks"></a>Observaciones

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapremovekey"></a><a name="removekey"></a>CRBMultiMap::RemoveKey

Llame a este método para quitar todos los elementos clave/valor de una clave determinada.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave que identifica los elementos que se van a eliminar.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de valores asociados a la clave dada.

### <a name="remarks"></a>Observaciones

`RemoveKey`elimina todos los elementos clave/valor que tienen una clave que coincide con la *clave*.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Consulte también

[CRBTree Clase](../../atl/reference/crbtree-class.md)<br/>
[Clase CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[CRBMap Class](../../atl/reference/crbmap-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
