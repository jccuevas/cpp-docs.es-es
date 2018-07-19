---
title: '&lt;hash_set&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <hash_set>
- std::<hash_set>
dev_langs:
- C++
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f163ef7d0e5ec05dd0f41c11ea77c558cfef4919
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955710"
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

|Hash_set (versión)|Hash_multiset (versión)|Descripción|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator!= (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Comprueba si el objeto hash_set o hash_multiset situado a la izquierda del operador no es igual que el objeto hash_set o hash_multiset situado a la derecha.|
|[operator== (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[operator== (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Comprueba si el objeto hash_set o hash_multiset situado a la izquierda del operador es igual que el objeto hash_set o hash_multiset situado a la derecha.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Hash_set (versión)|Hash_multiset (versión)|Descripción|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Intercambia los elementos de dos encabezados hash_sets o hash_multisets.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[hash_compare (Clase)](../standard-library/hash-compare-class.md)|Describe un objeto que se puede usar cualquiera de los contenedores asociativos hash: hash_map, hash_multimap, hash_set o hash_multiset: de forma predeterminada `Traits` objeto de parámetro para ordenar y hash de los elementos que contienen.|
|[hash_set (Clase)](../standard-library/hash-set-class.md)|Se usa para el almacenamiento y la recuperación de datos rápida de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave.|
|[hash_multiset (Clase)](../standard-library/hash-multiset-class.md)|Se usa para el almacenamiento y la recuperación de datos rápida de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
