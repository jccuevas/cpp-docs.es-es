---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: 83a0ad52735f92d731dafb32ad1be5a8278776b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447181"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Define la clase de plantilla de contenedor opcional y varias plantillas auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> opcional

**Espacio de nombres:** std

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Comprueba si el objeto `optional` en el lado izquierdo del operador es igual al objeto `optional` del lado derecho.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Comprueba si el objeto `optional` en el lado izquierdo del operador no es igual al objeto `optional` del lado derecho.|
|[operator<](../standard-library/optional-operators.md#op_lt)|Comprueba si el objeto `optional` en el lado izquierdo del operador es menor que el objeto `optional` del lado derecho.|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|Comprueba si el objeto `optional` en el lado izquierdo del operador es menor o igual que el objeto `optional` del lado derecho.|
|[operator>](../standard-library/optional-operators.md#op_gt)|Comprueba si el objeto `optional` en el lado izquierdo del operador es mayor que el objeto `optional` del lado derecho.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Comprueba si el objeto `optional` en el lado izquierdo del operador es mayor o igual que el objeto `optional` del lado derecho.|

> [!NOTE]
> Además de las comparaciones relacionales, \<los operadores opcionales de > también admiten la comparación con **nullopt** y. `T`

### <a name="functions"></a>Funciones

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Hace que un objeto sea opcional.|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>Clases y structs

|||
|-|-|
|[hash]()||
|[Clase opcional](../standard-library/optional-class.md)|Describe un objeto que puede contener o no un valor.|
|[Struct nullopt_t](../standard-library/nullopt-t-structure.md)|Describe un objeto que no contiene un valor.|
|[Clase bad_optional_access](../standard-library/bad-optional-access-class.md)|Describe un objeto que se inicia como una excepción para informar de un intento de obtener acceso a un valor que no existe.|

### <a name="objects"></a>de la empresa

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
