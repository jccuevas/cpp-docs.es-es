---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: 6bb2ca0cc14bcc4a9b9df9877902de9181e0a768
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258151"
---
# <a name="lthash_mapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Este encabezado está obsoleto. La alternativa es [\<unordered_map >](unordered-map.md).

Define las plantillas de clase de contenedor hash_map y hash_multimap y sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <hash_map>
```

### <a name="operators"></a>Operadores

|Versión de hash_map|Versión de hash_multimap|Descripción|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[Operator! = (hash_multimap)](hash-map-operators.md#op_neq_mm)|Comprueba si el objeto hash_map o hash_multimap del lado izquierdo del operador no es igual al objeto hash_map o hash_multimap del lado derecho.|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Comprueba si el objeto hash_map o hash_multimap del lado izquierdo del operador es igual al objeto hash_map o hash_multimap del lado derecho.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Versión de hash_map|Versión de hash_multimap|Descripción|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Intercambia los elementos de dos encabezados hash_map o hash_multimap.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[hash_compare (Clase)](hash-compare-class.md)|Describe un objeto que puede usar cualquiera de los contenedores asociativos hash (hash_map, hash_multimap, hash_set o hash_multiset) como un objeto de parámetro de `Traits` predeterminado para ordenar y aplicar un algoritmo hash a los elementos que contienen.|
|[value_compare (Clase)](value-compare-class.md)|Proporciona un objeto de función que puede comparar los elementos de hash_map al comparar los valores de sus claves para determinar su orden relativo en hash_map.|
|[hash_map (Clase)](hash-map-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor es único y un valor de datos asociado.|
|[hash_multimap (Clase)](hash-multimap-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor no necesita ser único y un valor de datos asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_map >

**Espacio de nombres:** stdext

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](cpp-standard-library-reference.md)
