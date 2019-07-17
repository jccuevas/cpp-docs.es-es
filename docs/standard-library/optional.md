---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: c73ad2ad94a5de29bc2c457fdf6ca8b9c783615c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268487"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Define la clase de plantilla contenedor opcional y varias plantillas auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<opcional >

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
> Además de comparación relacional, \<opcional > operadores también admiten la comparación con **nullopt** y `T`.

### <a name="functions"></a>Funciones

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Convierte un objeto opcional.|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>Clases y structs

|||
|-|-|
|[hash]()||
|[Clase opcional](../standard-library/optional-class.md)|Describe un objeto que puede o no puede contener un valor.|
|[nullopt_t Struct](../standard-library/nullopt-t-structure.md)|Describe un objeto que no contiene un valor.|
|[Clase bad_optional_access](../standard-library/bad-optional-access-class.md)|Describe un objeto que se inicia una excepción para informar de un intento de acceder a un valor no existe.|

### <a name="objects"></a>de la empresa

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
