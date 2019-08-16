---
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: 559bbff00b8e5204dd4f381abaf9987b4752db48
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452014"
---
# <a name="lthashsetgt"></a>&lt;hash_set&gt;

> [!NOTE]
> Este encabezado está obsoleto. La alternativa es la [clase unordered_set](../standard-library/unordered-set.md).

Define las clases de plantilla de contenedor hash_set y hash_multiset, así como sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <hash_set>
```

## <a name="remarks"></a>Comentarios

### <a name="operators"></a>Operadores

|Hash_set (versión)|Hash_multiset (versión)|DESCRIPCIÓN|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator!= (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Comprueba si el objeto hash_set o hash_multiset situado a la izquierda del operador no es igual que el objeto hash_set o hash_multiset situado a la derecha.|
|[operator== (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[operator== (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Comprueba si el objeto hash_set o hash_multiset situado a la izquierda del operador es igual que el objeto hash_set o hash_multiset situado a la derecha.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Hash_set (versión)|Hash_multiset (versión)|DESCRIPCIÓN|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Intercambia los elementos de dos encabezados hash_sets o hash_multisets.|

### <a name="classes"></a>Clases

|Clase|DESCRIPCIÓN|
|-|-|
|[hash_compare (Clase)](../standard-library/hash-compare-class.md)|Describe un objeto que puede usar cualquiera de los contenedores asociativos hash (hash_map, hash_multimap, hash_set o hash_multiset) como un objeto de parámetro predeterminado `Traits` para ordenar y aplicar un algoritmo hash a los elementos que contienen.|
|[hash_set (Clase)](../standard-library/hash-set-class.md)|Se usa para el almacenamiento y la recuperación de datos rápida de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave.|
|[hash_multiset (Clase)](../standard-library/hash-multiset-class.md)|Se usa para el almacenamiento y la recuperación de datos rápida de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
