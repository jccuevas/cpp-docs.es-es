---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 76b04c3c26f6ec49f1d816feaeec7e21312d79a9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246278"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

Define los tipos, funciones y operadores de las biblioteca estándar de C++ que facilitan la creación y administración de pares de objetos, que resultan útiles cuando se deben tratar dos objetos como si fueran uno solo.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<utility>

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Los pares se usan ampliamente en la biblioteca estándar de C++. Son necesarios como argumentos y valores de devolución para distintas funciones y como tipos de elemento para contenedores como [la clase map](../standard-library/map-class.md) y la [clase multimap](../standard-library/multimap-class.md). \<map> incluye automáticamente el encabezado \<utility> para ayudar en la administración de los elementos de tipo de par clave/valor.

> [!NOTE]
> El \<utilidad > encabezado utiliza la instrucción `#include <initializer_list>`. También hace referencia a `class tuple` tal como se define en \<tupla >.

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Formato de punto flotante para la conversión numérica primitivo.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Clase que contiene el tipo de un elemento `pair`.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Clase que contiene el recuento de elementos `pair`.|

### <a name="objects"></a>de la empresa

|||
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)||
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)||
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)||
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)||

### <a name="functions"></a>Funciones

|||
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|Devuelve el tipo.|
|[declval)](../standard-library/utility-functions.md#declval)|Evaluación de expresiones de la forma abreviada.|
|[exchange](../standard-library/utility-functions.md#exchange)|Asigna un nuevo valor a un objeto y devuelve su valor anterior.|
|[forward](../standard-library/utility-functions.md#forward)|Impide que el reenvío directo oculte el tipo de referencia (`lvalue` o `rvalue`) del argumento.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|Función que obtiene un elemento de un objeto `pair`.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Función del asistente de plantillas usada para construir objetos de tipo `pair`, donde los tipos de componente se basan en los tipos de datos pasados como parámetros.|
|[move](../standard-library/utility-functions.md#move)|Devuelve los argumentos pasados como referencia `rvalue`.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|Intercambia los elementos de dos objetos `pair`.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Convierte el valor en una cadena de caracteres.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Comprueba si el objeto de par del lado izquierdo del operador no es igual que el objeto de par del lado derecho.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Comprueba si el objeto de par del lado izquierdo del operador es igual que el objeto de par del lado derecho.|
|[operator\<](../standard-library/utility-operators.md#op_lt)|Comprueba si el objeto de par del lado izquierdo del operador es menor que el objeto de par del lado derecho.|
|[operator\<=](../standard-library/utility-operators.md#op_gt_eq)|Comprueba si el objeto de par del lado izquierdo del operador es menor o igual que el objeto de par del lado derecho.|
|[operator>](../standard-library/utility-operators.md#op_gt)|Comprueba si el objeto de par del lado izquierdo del operador es mayor que el objeto de par del lado derecho.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Comprueba si el objeto de par del lado izquierdo del operador es mayor o igual que el objeto de par del lado derecho.|

### <a name="structs"></a>Estructuras

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Un struct que se usa para `from_chars`.|
|[identity](../standard-library/identity-structure.md)|Estructura que proporciona una definición de tipo como parámetro de plantilla.|
|[revisión de in_place_t](../standard-library/in-place-t-struct.md)|También incluye structs `in_place_type_t` y `in_place_index_t`.|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Representa una secuencia de enteros.|
|[pair](../standard-library/pair-structure.md)|Tipo que proporciona la capacidad de tratar dos objetos como uno solo.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Un tipo que se utiliza para mantener independiente constructor y la sobrecarga de funciones.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Un struct que se usa para `to_chars`.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
