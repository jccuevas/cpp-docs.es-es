---
title: CRBMap Class
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 9e367ccc875eedf63e4f47018598662af2dfcf7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331404"
---
# <a name="crbmap-class"></a>CRBMap Class

Esta clase representa una estructura de asignación, mediante un árbol binario rojo-negro.

## <a name="syntax"></a>Sintaxis

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMap::CRBMap](#crbmap)|El constructor.|
|[CRBMap::-CRBMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Llame a este método para buscar `CRBMap` claves o valores en el objeto.|
|[CRBMap::RemoveKey](#removekey)|Llame a este método para `CRBMap` quitar un elemento del objeto, dada la clave.|
|[CRBMap::SetAt](#setat)|Llame a este método para insertar un par de elementos en el mapa.|

## <a name="remarks"></a>Observaciones

`CRBMap`proporciona compatibilidad con una matriz de asignación de cualquier tipo determinado, administrando una matriz ordenada de elementos clave y sus valores asociados. Cada clave solo puede tener un valor asociado. Los elementos (que constan de una clave y un valor) se almacenan en una estructura de árbol binario, mediante el método [CRBMap::SetAt.](#setat) Los elementos se pueden quitar mediante el [crBMap::RemoveKey](#removekey) método, que elimina el elemento con el valor de clave especificado.

El recorrido del árbol es posible con métodos como [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)y [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

Los *parámetros KTraits* y *VTraits* son clases de rasgos que contienen cualquier código suplementario necesario para copiar o mover elementos.

`CRBMap`se deriva de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario utilizando el algoritmo Rojo-Negro. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) es una variación que permite varios valores para cada clave. También se deriva `CRBTree`de , por lo `CRBMap`que comparte muchas características con .

Una alternativa `CRBMap` a `CRBMultiMap` ambos y es ofrecido por la [CAtlMap](../../atl/reference/catlmap-class.md) clase. Cuando solo es necesario almacenar un pequeño número de elementos, considere la posibilidad de usar la [clase CSimpleMap](../../atl/reference/csimplemap-class.md) en su lugar.

Para obtener una explicación más completa de las distintas clases de colección y sus características y características de rendimiento, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a>CRBMap::CRBMap

El constructor.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Tamaño de bloque.

### <a name="remarks"></a>Observaciones

El *nBlockSize* parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos. El valor predeterminado asignará espacio para 10 elementos a la vez.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a>CRBMap::-CRBMap

Destructor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

## <a name="crbmaplookup"></a><a name="lookup"></a>CRBMap::Lookup

Llame a este método para buscar `CRBMap` claves o valores en el objeto.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave que identifica el elemento que se va a buscar.

*value*<br/>
Variable que recibe el valor buscado.

### <a name="return-value"></a>Valor devuelto

La primera forma del método devuelve true si se encuentra la clave, de lo contrario false. La segunda y tercera formas devuelven un puntero a un [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Observaciones

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a>CRBMap::RemoveKey

Llame a este método para `CRBMap` quitar un elemento del objeto, dada la clave.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave correspondiente al par de elementos que desea quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si se encuentra y quita la clave, false en caso de error.

### <a name="remarks"></a>Observaciones

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a>CRBMap::SetAt

Llame a este método para insertar un par de elementos en el mapa.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
El valor de clave `CRBMap` que se va a agregar al objeto.

*value*<br/>
El valor que `CRBMap` se va a agregar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del par clave/valor del elemento en el `CRBMap` objeto.

### <a name="remarks"></a>Observaciones

`SetAt`reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave/valor.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los otros métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Consulte también

[CRBTree Clase](../../atl/reference/crbtree-class.md)<br/>
[Clase CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap Clase](../../atl/reference/crbmultimap-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
