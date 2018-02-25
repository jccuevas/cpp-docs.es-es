---
title: '&lt;hash_map&gt; | Microsoft Docs'
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <hash_map>
- std::<hash_map>
dev_langs:
- C++
helpviewer_keywords:
- hash_map header
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c50716912b42aace87b1132672331c86d9eae162
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Este encabezado está obsoleto. La alternativa es [ \<unordered_map >](unordered-map.md).

Define las clases de plantilla de contenedor hash_map y hash_multimap y sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

> #<a name="include-hashmap"></a>incluir < hash_map >

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

|||
|-|-|
|[Clase hash_compare](hash-compare-class.md)|Describe un objeto que se puede usar con cualquiera de los contenedores asociativos hash (hash_map, hash_multimap, hash_set o hash_multiset) como objeto de parámetro **Traits** predeterminado para ordenar y aplicar algoritmos hash a los elementos que contienen.|
|[Clase value_compare](value-compare-class.md)|Proporciona un objeto de función que puede comparar los elementos de hash_map al comparar los valores de sus claves para determinar su orden relativo en hash_map.|
|[Clase hash_map](hash-map-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor es único y un valor de datos asociado.|
|[Clase hash_multimap](hash-multimap-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor no necesita ser único y un valor de datos asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_map>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)  
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)  
[Referencia de biblioteca estándar de C++](cpp-standard-library-reference.md)  
