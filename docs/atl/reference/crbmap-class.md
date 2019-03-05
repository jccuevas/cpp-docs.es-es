---
title: CRBMap (clase)
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
ms.openlocfilehash: e5dedb26544bb2755bc74894cf36a622f5141f89
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301511"
---
# <a name="crbmap-class"></a>CRBMap (clase)

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
|[CRBMap::CRBMap](#crbmap)|El constructor.|
|[CRBMap::~CRBMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Llame a este método para buscar las claves o valores de la `CRBMap` objeto.|
|[CRBMap::RemoveKey](#removekey)|Llame a este método para quitar un elemento de la `CRBMap` objeto, dada la clave.|
|[CRBMap::SetAt](#setat)|Llame a este método para insertar un par de elementos en el mapa.|

## <a name="remarks"></a>Comentarios

`CRBMap` proporciona compatibilidad para una matriz de asignación de un tipo dado, administración de una matriz ordenada de elementos clave y sus valores asociados. Cada clave puede tener solo un valor asociado. Elementos (que consta de una clave y un valor) se almacenan en un árbol binario estructura, utilizando el [CRBMap::SetAt](#setat) método. Se pueden quitar los elementos mediante el [CRBMap::RemoveKey](#removekey) método, que elimina el elemento con el valor de clave especificado.

Recorrer el árbol se realiza con métodos como [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), y [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

El *KTraits* y *VTraits* parámetros son las clases de rasgos que contienen cualquier código complementario necesario para copiar o mover elementos.

`CRBMap` se deriva de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario mediante el algoritmo rojo-negro. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) es una variación que permite varios valores para cada clave. También se deriva de `CRBTree`y por lo tanto comparte muchas características con `CRBMap`.

Una alternativa a ambos `CRBMap` y `CRBMultiMap` ofrecida por la [CAtlMap](../../atl/reference/catlmap-class.md) clase. Cuando se necesita solo un pequeño número de elementos que se almacenará, considere el uso de la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase en su lugar.

Para obtener una explicación más completa de las distintas clases de colección y sus características y las características de rendimiento, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="crbmap"></a>  CRBMap::CRBMap

El constructor.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
El tamaño de bloque.

### <a name="remarks"></a>Comentarios

El *nBlockSize* parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayor tamaño de bloque reduce las llamadas a rutinas de asignación de memoria, pero usa más recursos. El valor predeterminado asigna espacio de 10 elementos a la vez.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMap::~CRBMap

Destructor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

##  <a name="lookup"></a>  CRBMap::Lookup

Llame a este método para buscar las claves o valores de la `CRBMap` objeto.

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

El primer formulario del método devuelve true si se encuentra la clave, en caso contrario, false. Los formularios de la segundo y terceros devuelven un puntero a un [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Comentarios

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

##  <a name="removekey"></a>  CRBMap::RemoveKey

Llame a este método para quitar un elemento de la `CRBMap` objeto, dada la clave.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave correspondiente a la par de elementos que desea quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la clave se encuentra y quita, false en caso de error.

### <a name="remarks"></a>Comentarios

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

##  <a name="setat"></a>  CRBMap::SetAt

Llame a este método para insertar un par de elementos en el mapa.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
El valor de clave para agregar a la `CRBMap` objeto.

*value*<br/>
Valor que se agrega a la `CRBMap` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del par clave-valor elemento en el `CRBMap` objeto.

### <a name="remarks"></a>Comentarios

`SetAt` reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave-valor.

Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Vea también

[CRBTree (clase)](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap (clase)](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap (clase)](../../atl/reference/crbmultimap-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
