---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: bce31811c98d351f3c561b3136d41f7ed23d13e0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687257"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Define la plantilla de clase contenedora `optional` y varias plantillas auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<optional >

**Espacio de nombres:** std

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Comprueba si un objeto es igual a otro objeto.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Comprueba si un objeto no es igual a otro objeto.|
|[operator<](../standard-library/optional-operators.md#op_lt)|Comprueba si el objeto de la izquierda es menor que el objeto de la derecha.|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|Comprueba si el objeto de la izquierda es menor o igual que el objeto de la derecha.|
|[operator>](../standard-library/optional-operators.md#op_gt)|Comprueba si el objeto de la izquierda es mayor que el objeto de la derecha.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Comprueba si el objeto de la izquierda es mayor o igual que el objeto de la derecha.|

> [!NOTE]
> Además de las comparaciones relacionales, \<optional operadores de > también admiten la comparación con **nullopt** y `T`.

### <a name="functions"></a>Funciones

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Hace que un objeto sea opcional.|
|[swap](../standard-library/optional-functions.md#swap)|Intercambia los valores contenidos de dos objetos `optional`.|

### <a name="classes-and-structs"></a>Clases y structs

|||
|-|-|
|hash|Devuelve un hash del objeto contenido.|
|[clase opcional](../standard-library/optional-class.md)|Describe un objeto que puede contener o no un valor.|
|[struct nullopt_t](../standard-library/nullopt-t-structure.md)|Describe un objeto que no contiene un valor.|
|[clase bad_optional_access](../standard-library/bad-optional-access-class.md)|Describe un objeto que se inicia como una excepción para informar de un intento de obtener acceso a un valor que no existe.|

### <a name="objects"></a>de la empresa

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|Instancia de `nullopt_t` para las comparaciones.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
