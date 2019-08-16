---
title: '&lt;Variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 7a812ccc3c8cb2a660c01ad2b17ea75b5d5c9542
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268447"
---
# <a name="ltvariantgt"></a>&lt;Variant&gt;

Un objeto variant contiene y administra un valor. Si la variante contiene un valor, ese tipo de valor debe ser uno de los tipos de argumento de plantilla dado la variante. Estos argumentos de plantilla se denominan alternativas.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<variante >

**Espacio de nombres:** std

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|Comprueba si el objeto variant en el lado izquierdo del operador es igual que el objeto variant en el lado derecho.|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|Comprueba si el objeto variant en el lado izquierdo del operador no es igual que el objeto variant en el lado derecho.|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|Comprueba si el objeto variant en el lado izquierdo del operador es menor que el objeto variant en el lado derecho.|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|Comprueba si el objeto de la variante en el lado izquierdo del operador es menor o igual que el objeto variant en el lado derecho.|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|Comprueba si el objeto variant en el lado izquierdo del operador es mayor que el objeto variant en el lado derecho.|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|Comprueba si el objeto variant en el lado izquierdo del operador es mayor o igual que el objeto variant en el lado derecho.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|Obtiene la variante de un objeto.|
|[get_if](../standard-library/variant-functions.md#get_if)|Obtiene la variante de un objeto, si existe.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|Devolver **true** si existe una variante.|
|[swap](../standard-library/variant-functions.md#swap)|Intercambia un **variante**.|
|[Visite](../standard-library/variant-functions.md#visit)|Se desplaza a la siguiente **variante**.|

### <a name="classes"></a>Clases

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|Objetos que se produce a accesos no válido del informe en el valor de un objeto variant.|
|[Variant](../standard-library/variant.md)|Un objeto que contiene un valor de uno de sus tipos alternativos o ningún valor.|

### <a name="structs"></a>Estructuras

|||
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|Un tipo alternativo para una variante para hacer que se puede construir el valor predeterminado de tipo variant.|
|[uses_allocator)](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|Ayuda a los objetos de tipo variant.|
|[variant_size](../standard-library/variant-size-structure.md)|Ayuda a los objetos de tipo variant.|

### <a name="objects"></a>de la empresa

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
