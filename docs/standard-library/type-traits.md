---
title: '&lt;type_traits&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <type_traits>
dev_langs:
- C++
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fed2cad9c96b20313617ef57e4373de16712aa34
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218857"
---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;

Define las plantillas que proporcionan constantes en tiempo de compilación que aportan información sobre las propiedades de sus argumentos de tipo o crean tipos transformados.

## <a name="syntax"></a>Sintaxis

```cpp
#include <type_traits>
```

## <a name="remarks"></a>Comentarios

Las clases y plantillas de \<type_traits > se utilizan para admitir la inferencia, clasificación y transformación en tiempo de compilación para detectar errores relacionados con el tipo y que le ayudarán a optimizar el código genérico. Estas clases y plantillas incluyen rasgos de tipo unario que describen una propiedad de un tipo, rasgos de tipo binario que describen la relación entre los tipos y rasgos de transformación que modifican una propiedad de un tipo.

Para admitir rasgos de tipo, se define una clase auxiliar, `integral_constant`. Tiene especializaciones de plantilla `true_type` y `false_type` que forman las clases base para los predicados de tipo. Un *predicado de tipo* es una plantilla que toma uno o más argumentos de tipo. Cuando un predicado de tipo *es true*, se deriva públicamente (ya sea de forma directa o indirecta) de [true_type](../standard-library/type-traits-typedefs.md#true_type). Cuando un predicado de tipo *es false*, se deriva públicamente (ya sea de forma directa o indirecta) de [false_type](../standard-library/type-traits-typedefs.md#false_type).

Un *modificador de tipo* o *rasgo de transformación* es una plantilla que toma uno o más argumentos de plantilla y tiene un miembro `type`, que es un sinónimo del tipo modificado.

### <a name="alias-templates"></a>Plantillas de alias

Para simplificar las expresiones de rasgos de tipo, se proporcionan [plantillas de alias](../cpp/aliases-and-typedefs-cpp.md) para `typename some_trait<T>::type`, donde " `some_trait`" es el nombre de clase de la plantilla. Por ejemplo, [add_const](../standard-library/add-const-class.md) tiene la plantilla de alias para su tipo `add_const_t` definida así:

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

|||||
|-|-|-|-|
|add_const_t|aligned_storage_t|make_signed_t|remove_pointer_t|
|add_cv_t|aligned_union_t|make_unsigned_t|remove_reference_t|
|add_lvalue_reference_t|common_type_t|remove_all_extents_t|remove_volatile_t|
|add_pointer_t|conditional_t|remove_const_t|result_of_t|
|add_rvalue_reference_t|decay_t|remove_cv_t|underlying_type_t|
|add_volatile_t|enable_if_t|remove_extent_t||

### <a name="classes"></a>Clases

Definiciones de tipos y clase auxiliar

|||
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Crea una constante entera a partir de un tipo y un valor.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Contiene la constante integral con valor true.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Contiene la constante integral con valor false.|

Categorías de tipo principal

|||
|-|-|
|[is_void](../standard-library/is-void-class.md)|Comprueba si el tipo es **void**.|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Comprueba si el tipo es `std::nullptr_t`.|
|[is_integral](../standard-library/is-integral-class.md)|Comprueba si el tipo es integral.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|Comprueba si el tipo es un punto flotante.|
|[is_array](../standard-library/is-array-class.md)|Comprueba si el tipo es una matriz.|
|[is_pointer](../standard-library/is-pointer-class.md)|Comprueba si el tipo es un puntero.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Comprueba si el tipo es una referencia a un valor L.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Comprueba si el tipo es una referencia a un valor R.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Comprueba si el tipo es un puntero a un objeto miembro.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Comprueba si el tipo es un puntero a una función miembro.|
|[is_enum](../standard-library/is-enum-class.md)|Comprueba si el tipo es una enumeración.|
|[is_union](../standard-library/is-union-class.md)|Comprueba si el tipo es una unión.|
|[is_class](../standard-library/is-class-class.md)|Comprueba si el tipo es una clase.|
|[is_function](../standard-library/is-function-class.md)|Comprueba si el tipo es un tipo de función.|

Categorías de tipo compuesto

|||
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|Comprueba si el tipo es una referencia.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Comprueba si el tipo es aritmético.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|Comprueba si el tipo es **void** o aritmético.|
|[is_object](../standard-library/is-object-class.md)|Comprueba si el tipo es un tipo de objeto.|
|[is_scalar](../standard-library/is-scalar-class.md)|Comprueba si el tipo es escalar.|
|[is_compound](../standard-library/is-compound-class.md)|Comprueba si el tipo no es escalar.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Comprueba si el tipo es un puntero a un miembro.|

Propiedades de tipo

|||
|-|-|
|[is_const](../standard-library/is-const-class.md)|Comprueba si el tipo es **const**.|
|[is_volatile](../standard-library/is-volatile-class.md)|Comprueba si el tipo es **volátil**.|
|[is_trivial](../standard-library/is-trivial-class.md)|Comprueba si el tipo es trivial.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Comprueba si el tipo se puede copiar de manera trivial.|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Comprueba si el tipo es un tipo de diseño estándar.|
|[is_pod](../standard-library/is-pod-class.md)|Comprueba si el tipo es POD.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|Comprueba si el tipo puede ser una variable `constexpr` o se puede usar en una función `constexpr`.|
|[is_empty](../standard-library/is-empty-class.md)|Comprueba si el tipo es una clase vacía.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Comprueba si el tipo es una clase polimórfica.|
|[is_abstract](../standard-library/is-abstract-class.md)|Comprueba si el tipo es una clase abstracta.|
|[is_final](../standard-library/is-final-class.md)|Comprueba si el tipo es un tipo de clase marcado como `final`.|
|[is_signed](../standard-library/is-signed-class.md)|Comprueba si el tipo es un entero con signo.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|Comprueba si el tipo es un entero sin signo.|
|[is_constructible](../standard-library/is-constructible-class.md)|Comprueba si el tipo se puede construir con los tipos de argumento especificados.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Comprueba si el tipo tiene un constructor predeterminado.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Comprueba si el tipo tiene un constructor de copia.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Comprueba si el tipo tiene un constructor de movimiento.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Comprueba si al primer tipo puede asignarse un valor del segundo tipo.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Comprueba si a un tipo puede asignarse un valor de referencia constante del tipo.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Comprueba si a un tipo puede asignarse un valor de referencia R del tipo.|
|[is_destructible](../standard-library/is-destructible-class.md)|Comprueba si el tipo se puede destruir.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Comprueba si el tipo no usa ninguna operación no trivial cuando se construye usando los tipos especificados.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Comprueba si el tipo no usa ninguna operación no trivial cuando se construye de manera predeterminada.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Comprueba si el tipo no usa ninguna operación no trivial cuando se aplica el constructor de copias.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Comprueba si el tipo no usa ninguna operación no trivial cuando se aplica el constructor de movimiento.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Comprueba si los tipos se pueden asignar y la asignación no usa ninguna operación no trivial.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Comprueba si el tipo se puede asignar mediante copia y la asignación no usa ninguna operación no trivial.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Comprueba si el tipo se puede asignar mediante movimiento y la asignación no usa ninguna operación no trivial.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Comprueba si se puede destruir el tipo y el destructor no usa ninguna operación no trivial.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Comprueba si el tipo se puede construir y se sabe que no se inicia cuando se construye usando los tipos especificados.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Comprueba si el tipo se puede construir de forma predeterminada y se sabe que no se inicia cuando se construye de forma predeterminada.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Comprueba si el tipo se puede construir mediante copia y se sabe que el constructor de copias no se inicia.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Comprueba si el tipo se puede construir mediante movimiento y se sabe que el constructor de movimiento no se inicia.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Comprueba si el tipo se puede asignar mediante el tipo especificado y se sabe que la asignación no se inicia.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Comprueba si el tipo se puede construir mediante copia y se sabe que la asignación no se inicia.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Comprueba si el tipo se puede asignar mediante movimiento y se sabe que la asignación no se inicia.|
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Comprueba si el tipo se puede destruir y se sabe que el destructor no se inicia.|
|[has_virtual_destructor](https://msdn.microsoft.com/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|Comprueba si el tipo tiene un destructor virtual.|

Consultas de propiedad de tipo

|||
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|Obtiene la alineación de un tipo.|
|[rank](../standard-library/rank-class.md)|Obtiene el número de dimensiones de matriz.|
|[extent](../standard-library/extent-class.md)|Obtiene el número de elementos de la dimensión de la matriz especificada.|

Relaciones de tipos

|||
|-|-|
|[is_same](../standard-library/is-same-class.md)|Comprueba si dos tipos son iguales.|
|[is_base_of](../standard-library/is-base-of-class.md)|Comprueba si un tipo es la base de otro.|
|[is_convertible](../standard-library/is-convertible-class.md)|Comprueba si un tipo es convertible en otro.|

Modificaciones de const y volatile

|||
|-|-|
|[add_const](../standard-library/add-const-class.md)|Genera un **const** tipo del tipo.|
|[add_volatile](../standard-library/add-volatile-class.md)|Genera un **volátil** tipo del tipo.|
|[add_cv](../standard-library/add-cv-class.md)|Genera un **const volatile** tipo del tipo.|
|[remove_const](../standard-library/remove-const-class.md)|Genera un tipo no constante a partir del tipo.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|Genera un tipo no volátil a partir del tipo.|
|[remove_cv](../standard-library/remove-cv-class.md)|Genera un tipo no constante y no volátil a partir del tipo.|

Modificaciones de referencia

|||
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Genera una referencia al tipo a partir del tipo.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Genera una referencia de valor R al tipo a partir del tipo.|
|[remove_reference](../standard-library/remove-reference-class.md)|Genera un tipo sin referencia a partir del tipo.|

Modificaciones de signo

|||
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|Genera el tipo si tiene signo o el tipo con signo más pequeño igual o superior en tamaño al tipo.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|Genera el tipo si no tiene signo o el tipo con signo más pequeño igual o superior en tamaño al tipo.|

Modificaciones de matriz

|||
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Genera un tipo que no es de matriz a partir de un tipo de matriz.|
|[remove_extent](../standard-library/remove-extent-class.md)|Genera el tipo de elemento a partir de un tipo de matriz.|

Modificaciones de puntero

|||
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|Genera un puntero al tipo a partir del tipo.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|Genera un tipo a partir de un puntero al tipo.|

Otras transformaciones

|||
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|Asigna memoria sin inicializar para un tipo alineado.|
|[aligned_union](../standard-library/aligned-union-class.md)|Asigna memoria sin inicializar para una unión alineada con un destructor o un constructor no trivial.|
|[common_type](../standard-library/common-type-class.md)|Genera el tipo común de todos los tipos del paquete de parámetros.|
|[conditional](../standard-library/conditional-class.md)|Si la condición es true, genera el primer tipo especificado, de lo contrario, el segundo tipo especificado.|
|[decay](../standard-library/decay-class.md)|Genera el tipo tal y como se pasa por valor. Crea un tipo que no es de referencia, const o volatile, o bien convierte un puntero al tipo.|
|[enable_if](../standard-library/enable-if-class.md)|Si la condición es true, genera el tipo especificado, de lo contrario, no genera ningún tipo.|
|[result_of](../standard-library/result-of-class.md)|Determina el tipo de valor devuelto del tipo que se puede llamar que toma los tipos de argumento especificados.|
|[underlying_type](../standard-library/underlying-type-class.md)|Genera el tipo entero subyacente para un tipo de enumeración.|

## <a name="see-also"></a>Vea también

[\<functional>](../standard-library/functional.md)<br/>
