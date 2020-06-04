---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: eaae94bcffcda6e113001dd7070bcc80e7c14d09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458079"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

Define los tipos, funciones y operadores de las biblioteca estándar de C++ que facilitan la creación y administración de pares de objetos, que resultan útiles cuando se deben tratar dos objetos como si fueran uno solo.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<utility>

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Los pares se usan ampliamente en la biblioteca estándar de C++. Son necesarios como argumentos y valores de devolución para distintas funciones y como tipos de elemento para contenedores como [la clase map](../standard-library/map-class.md) y la [clase multimap](../standard-library/multimap-class.md). \<map> incluye automáticamente el encabezado \<utility> para ayudar en la administración de los elementos de tipo de par clave/valor.

> [!NOTE]
> El \<encabezado > de la utilidad utiliza `#include <initializer_list>`la instrucción. También hace referencia a `class tuple` tal y como \<se define en la tupla >.

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Formato de punto flotante para la conversión numérica primitiva.|
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
|[declval (](../standard-library/utility-functions.md#declval)|Evaluación de Expresiones abreviadas.|
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
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Struct que se utiliza `from_chars`para.|
|[identity](../standard-library/identity-structure.md)|Estructura que proporciona una definición de tipo como parámetro de plantilla.|
|[in_place_t](../standard-library/in-place-t-struct.md)|También incluye Structs `in_place_type_t` y `in_place_index_t`.|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Representa una secuencia de enteros.|
|[pair](../standard-library/pair-structure.md)|Tipo que proporciona la capacidad de tratar dos objetos como uno solo.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Tipo que se usa para mantener la sobrecarga de constructor y función independiente.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Struct que se utiliza `to_chars`para.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
