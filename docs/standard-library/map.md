---
title: '&lt;map&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 96ca19b2562c3f145555c3c1b1d8db4fc700ed91
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243319"
---
# <a name="ltmapgt"></a>&lt;map&gt;

Define la asignación y la asignación múltiple de clases de plantilla de contenedor, así como sus plantillas auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<map>

**Espacio de nombres:** std

> [!NOTE]
> El \<map > biblioteca también utiliza el `#include <initializer_list>` instrucción.

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|Versión de asignación|Versión de asignación múltiple|DESCRIPCIÓN|
|-----------------|----------------------|-----------------|
|[operator!= (map)](../standard-library/map-operators.md#op_neq)|[operator!= (multimap)](../standard-library/map-operators.md#op_neq)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador no es igual que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator< (map)](../standard-library/map-operators.md#op_eq_eq)|[operator< (multimap)](../standard-library/map-operators.md#op_eq_eq)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es menor que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator<= (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es menor o igual que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es igual que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator> (map)](../standard-library/map-operators.md#op_gt)|[operator> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es mayor que el objeto de asignación o asignación múltiple del lado derecho.|
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es mayor o igual que el objeto de asignación o asignación múltiple del lado derecho.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Versión de asignación|Versión de asignación múltiple|DESCRIPCIÓN|
|-----------------|----------------------|-----------------|
|[swap (mapa)](../standard-library/map-functions.md#swap)|[swap (mapa múltiple)](../standard-library/map-functions.md#swap_multimap)|Intercambia los elementos de dos asignaciones o asignaciones múltiples.|

### <a name="classes"></a>Clases

|||
|-|-|
|[value_compare (Clase)](../standard-library/value-compare-class-map.md)|Proporciona un objeto de función que puede comparar los elementos de una asignación comparando los valores de sus claves para determinar su orden relativo en la asignación.|
|[Clase map](../standard-library/map-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que cada uno de los elementos tiene una clave única con la que se ordenan automáticamente los datos.|
|[Clase multimap](../standard-library/multimap-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que cada uno de los elementos tiene una clave con la que se ordenan automáticamente los datos y no es necesario que las claves tengan valores únicos.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
