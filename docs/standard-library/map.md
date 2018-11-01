---
title: '&lt;map&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 727938b09ae60fd72a2421c2b800d8910f82934e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659854"
---
# <a name="ltmapgt"></a>&lt;map&gt;

Define la asignación y la asignación múltiple de clases de plantilla de contenedor, así como sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <map>

```

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|Versión de asignación|Versión de asignación múltiple|Descripción|
|-----------------|----------------------|-----------------|
|[operator!= (map)](../standard-library/map-operators.md#op_neq)|[operator!= (multimap)](../standard-library/map-operators.md#op_neq)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador no es igual que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator< (map)](../standard-library/map-operators.md#op_eq_eq)|[operator< (multimap)](../standard-library/map-operators.md#op_eq_eq)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es menor que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator<= (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es menor o igual que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es igual que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator> (map)](../standard-library/map-operators.md#op_gt)|[operator> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es mayor que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es mayor o igual que el objeto de asignación o asignación múltiple del lado derecho.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Versión de asignación|Versión de asignación múltiple|Descripción|
|-----------------|----------------------|-----------------|
|[swap (mapa)](../standard-library/map-functions.md#swap)|[swap (mapa múltiple)](../standard-library/map-functions.md#swap_multimap)|Intercambia los elementos de dos asignaciones o asignaciones múltiples.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[value_compare (Clase)](../standard-library/value-compare-class-map.md)|Proporciona un objeto de función que puede comparar los elementos de una asignación comparando los valores de sus claves para determinar su orden relativo en la asignación.|
|[Clase map](../standard-library/map-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que cada uno de los elementos tiene una clave única con la que se ordenan automáticamente los datos.|
|[Clase multimap](../standard-library/multimap-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que cada uno de los elementos tiene una clave con la que se ordenan automáticamente los datos y no es necesario que las claves tengan valores únicos.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
