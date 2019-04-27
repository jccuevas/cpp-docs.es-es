---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: 5a7ea891a314d69b8bc3378edce9fa0de2d89ace
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159501"
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Este encabezado está obsoleto. La alternativa es [ \<unordered_map >](unordered-map.md).

Define las clases de plantilla de contenedor hash_map y hash_multimap y sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```
#include <hash_map>
```

### <a name="operators"></a>Operadores

|Versión de hash_map|Versión de hash_multimap|Descripción|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Comprueba si el objeto hash_map o hash_multimap del lado izquierdo del operador no es igual al objeto hash_map o hash_multimap del lado derecho.|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Comprueba si el objeto hash_map o hash_multimap del lado izquierdo del operador es igual al objeto hash_map o hash_multimap del lado derecho.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Versión de hash_map|Versión de hash_multimap|Descripción|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Intercambia los elementos de dos encabezados hash_map o hash_multimap.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[hash_compare (Clase)](hash-compare-class.md)|Describe un objeto que se puede usar cualquiera de los contenedores asociativos hash: hash_map, hash_multimap, hash_set o hash_multiset: de forma predeterminada `Traits` objeto de parámetro para ordenar y hash de los elementos que contienen.|
|[value_compare (Clase)](value-compare-class.md)|Proporciona un objeto de función que puede comparar los elementos de hash_map al comparar los valores de sus claves para determinar su orden relativo en hash_map.|
|[Clase hash_map](hash-map-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor es único y un valor de datos asociado.|
|[Clase hash_multimap](hash-multimap-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor no necesita ser único y un valor de datos asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_map>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](cpp-standard-library-reference.md)
