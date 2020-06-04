---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: fed6219c483bdade0132d5faae8b6597bcc5d732
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686467"
---
# <a name="ltsetgt"></a>&lt;set&gt;

Define las plantillas de clase contenedoras set y MultiSet, así como sus plantillas auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<set>

**Espacio de nombres:** std

> [!NOTE]
> La biblioteca de > de \<set también utiliza la instrucción `#include <initializer_list>`.

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|Versión set|Versión multiset|Descripción|
|-|-|-|
|[operator!= (set)](../standard-library/set-operators.md#op_neq)|[operator!= (multiset)](../standard-library/set-operators.md#op_neq)|Comprueba si el objeto set o multiset a la izquierda del operador no es igual que el objeto set o multiset situado a la derecha del operador.|
|[operator< (set)](../standard-library/set-operators.md#op_lt)|[operator< (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es menor que el objeto set o multiset situado a la derecha del operador.|
|[operator<= (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es menor o igual que el objeto set o multiset situado a la derecha del operador.|
|[operator== (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es igual que el objeto set o multiset situado a la derecha del operador.|
|[operator> (set)](../standard-library/set-operators.md#op_gt)|[operator> (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor que el objeto set o multiset situado a la derecha del operador.|
|[operator>= (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor o igual que el objeto set o multiset situado a la derecha del operador.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Versión set|Versión multiset|Descripción|
|-|-|-|
|[swap](../standard-library/set-functions.md#swap)|[swap (conjunto mútiple)](../standard-library/set-functions.md#swap_multiset)|Intercambia los elementos de dos sets o multisets.|

### <a name="classes"></a>Clases

|||
|-|-|
|[set (Clase)](../standard-library/set-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave según los cuales se ordenan automáticamente los datos.|
|[multiset (Clase)](../standard-library/multiset-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos no tienen que ser únicos y en la que sirven como valores de clave según los cuales se ordenan automáticamente los datos.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
