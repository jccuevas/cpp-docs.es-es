---
title: hash_compare (Clase)
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: 4fb44a371630a66275f6ef59a0bf66b4cb73a71f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689555"
---
# <a name="hash_compare-class"></a>hash_compare (Clase)

La plantilla de clase describe un objeto que puede usar cualquiera de los contenedores asociativos hash (hash_map, hash_multimap, hash_set o hash_multiset) como objeto de parámetro **traits** predeterminado para ordenar y aplicar un algoritmo hash a los elementos que contienen.

## <a name="syntax"></a>Sintaxis

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>Comentarios

Cada contenedor asociativo hash almacena un objeto traits hash de tipo `Traits` (un parámetro de plantilla). Puede derivar una clase de una especialización de hash_compare para reemplazar de forma selectiva ciertas funciones y objetos o puede proporcionar su propia versión de esta clase si cumple ciertos requisitos mínimos. En concreto, para un objeto hash_comp de tipo `hash_compare<Key, Traits>`, los contenedores anteriores requieren el siguiente comportamiento:

- Para todos los valores `key` de tipo `Key`, la llamada a **hash_comp**(`key`) actúa como una función hash, que produce una distribución de valores de tipo `size_t`. La función suministrada por hash_compare devuelve `key`.

- Para cualquier valor `key1` de tipo `Key` que preceda a `key2` en la secuencia y que tenga el mismo valor hash (valor devuelto por la función hash), **hash_comp**(`key2`, `key1`) es false. La función debe imponer una ordenación total en los valores de tipo `Key`. La función proporcionada por hash_compare devuelve *COMP*(`key2`, `key1`) `,` donde *COMP* es un objeto almacenado de tipo `Traits` que se puede especificar al construir el objeto hash_comp. En el caso del tipo de parámetro `Traits` predeterminado `less<Key>`, las claves de ordenación nunca disminuyen en el valor.

- La constante de tipo entero `bucket_size` especifica el número medio de elementos por "bucket" (entrada de tabla hash) que el contenedor debe intentar no superar. Debe ser mayor que cero. El valor proporcionado por hash_compare es 4.

- La constante de tipo entero `min_buckets` especifica el número mínimo de depósitos que se deben mantener en la tabla hash. Debe ser una potencia de dos y mayor que cero. El valor proporcionado por hash_compare es 8.

## <a name="example"></a>Ejemplo

Vea los ejemplos de [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) y [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) para ver ejemplos sobre cómo declarar y usar hash_compare.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_map>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
