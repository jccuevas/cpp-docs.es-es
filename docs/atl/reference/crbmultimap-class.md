---
title: CRBMultiMap (clase)
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
ms.openlocfilehash: 03a9639e8b0b3d11a414e5db0ce874d7ca8f2d45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278142"
---
# <a name="crbmultimap-class"></a>CRBMultiMap (clase)

Esta clase representa una estructura de asignación que permite que cada clave puede asociarse con más de un valor, utilizando un árbol binario rojo-negro.

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
El tipo de elemento de clave.

*V*<br/>
El tipo de elemento de valor.

*KTraits*<br/>
El código utilizado para copiar o mover los elementos clave. Consulte [CElementTraits (clase)](../../atl/reference/celementtraits-class.md) para obtener más detalles.

*VTraits*<br/>
El código utilizado para copiar o mover elementos de valor.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|El constructor.|
|[CRBMultiMap::~CRBMultiMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Llame a este método para buscar la posición del primer elemento con una clave determinada.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Llame a este método para obtener el valor asociado con una clave determinada y actualice el valor de posición.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Llame a este método para obtener el elemento asociado con una clave determinada y actualice el valor de posición.|
|[CRBMultiMap::Insert](#insert)|Llame a este método para insertar un par de elementos en el mapa.|
|[CRBMultiMap::RemoveKey](#removekey)|Llame a este método para quitar todos los elementos clave/valor de una clave determinada.|

## <a name="remarks"></a>Comentarios

`CRBMultiMap` proporciona compatibilidad para una matriz de asignación de un tipo dado, administración de una matriz ordenada de elementos clave y valores. A diferencia de la [CRBMap](../../atl/reference/crbmap-class.md) (clase), cada clave puede asociarse con más de un valor.

Elementos (que consta de una clave y un valor) se almacenan en un árbol binario estructura, utilizando el [CRBMultiMap::Insert](#insert) método. Se pueden quitar los elementos mediante el [CRBMultiMap::RemoveKey](#removekey) método, que elimina todos los elementos que coinciden con la clave especificada.

Recorrer el árbol se realiza con métodos como [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), y [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Obtener acceso a la potencialmente de varios valores por clave es posible usar el [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), y [CRBMultiMap::GetNextWithKey ](#getnextwithkey) métodos. Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap) para ver una ilustración de esto en la práctica.

El *KTraits* y *VTraits* parámetros son las clases de rasgos que contienen cualquier código complementario necesario para copiar o mover elementos.

`CRBMultiMap` se deriva de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario mediante el algoritmo rojo-negro. Una alternativa a `CRBMultiMap` y `CRBMap` ofrecida por la [CAtlMap](../../atl/reference/catlmap-class.md) clase. Cuando se necesita solo un pequeño número de elementos que se almacenará, considere el uso de la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase en su lugar.

Para obtener una explicación más completa de las distintas clases de colección y sus características y las características de rendimiento, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="crbmultimap"></a>  CRBMultiMap::CRBMultiMap

El constructor.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
El tamaño de bloque.

### <a name="remarks"></a>Comentarios

El *nBlockSize* parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayor tamaño de bloque reduce las llamadas a rutinas de asignación de memoria, pero usa más recursos. El valor predeterminado asigna espacio de 10 elementos a la vez.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMultiMap::~CRBMultiMap

Destructor.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey

Llame a este método para buscar la posición del primer elemento con una clave determinada.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave que identifica el elemento que se encuentra.

### <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, valor NULL en caso contrario, devuelve la posición del primer elemento de pares clave-valor.

### <a name="remarks"></a>Comentarios

Una clave en el `CRBMultiMap` puede tener uno o varios de los valores asociados. Este método proporcionará el valor de la posición del primer valor (que, de hecho, sea el único valor) asociado a esa clave concreto. Devuelve el valor de posición, a continuación, puede usarse con [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) o [CRBMultiMap::GetNextWithKey](#getnextwithkey) para obtener el valor y actualizar la posición.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey

Llame a este método para obtener el valor asociado con una clave determinada y actualice el valor de posición.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*pos*<br/>
El valor de posición, obtenido con o bien una llamada a [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) o [CRBMultiMap::GetNextWithKey](#getnextwithkey), o una llamada anterior a `GetNextValueWithKey`.

*key*<br/>
Especifica la clave que identifica el elemento que se encuentra.

### <a name="return-value"></a>Valor devuelto

Devuelve el par de elementos asociado con la clave especificada.

### <a name="remarks"></a>Comentarios

El valor de posición se actualiza para señalar al siguiente valor asociado con la clave. Si no hay más valores, el valor de posición se establece en NULL.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey

Llame a este método para obtener el elemento asociado con una clave determinada y actualice el valor de posición.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*pos*<br/>
El valor de posición, obtenido con o bien una llamada a [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) o [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), o una llamada anterior a `GetNextWithKey`.

*key*<br/>
Especifica la clave que identifica el elemento que se encuentra.

### <a name="return-value"></a>Valor devuelto

Devuelve el siguiente [CRBTree::CPair clase](crbtree-class.md#cpair_class) elemento asociado con la clave especificada.

### <a name="remarks"></a>Comentarios

El valor de posición se actualiza para señalar al siguiente valor asociado con la clave. Si no hay más valores, el valor de posición se establece en NULL.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

##  <a name="insert"></a>  CRBMultiMap::Insert

Llame a este método para insertar un par de elementos en el mapa.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
El valor de clave para agregar a la `CRBMultiMap` objeto.

*value*<br/>
Valor que se agrega a la `CRBMultiMap` objeto asociado *clave*.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del par clave-valor elemento en el `CRBMultiMap` objeto.

### <a name="remarks"></a>Comentarios

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="removekey"></a>  CRBMultiMap::RemoveKey

Llame a este método para quitar todos los elementos clave/valor de una clave determinada.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave que identifica los elementos que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de valores asociados con la clave especificada.

### <a name="remarks"></a>Comentarios

`RemoveKey` Elimina todos los elementos de pares clave-valor que tienen una clave que coincida con *clave*.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Vea también

[CRBTree (clase)](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap (clase)](../../atl/reference/catlmap-class.md)<br/>
[CRBMap (clase)](../../atl/reference/crbmap-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
