---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: ed90273fe293ae2e08c3c91762c12c42bb368c16
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688762"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

Define la plantilla de clase valarray y numerosas plantillas y funciones de clase auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

> [!NOTE]
> La biblioteca de > de \<valarray usa la instrucción ' #include < initializer_list > '.

## <a name="remarks"></a>Comentarios

A estas funciones y plantillas de clase se les permite una latitud inusual con el fin de mejorar el rendimiento. En concreto, cualquier función que devuelva el tipo `valarray<T1>` puede devolver un objeto de algún otro tipo T2. En ese caso, cualquier función que acepte uno o más argumentos de tipo `valarray<T2>` debe tener sobrecargas que acepten combinaciones arbitrarias de esos argumentos, cada uno reemplazado por un argumento de tipo T2.

## <a name="members"></a>Miembros

### <a name="functions"></a>Funciones

|||
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al valor absoluto de los elementos de la valarray de entrada.|
|[acos](../standard-library/valarray-functions.md#acos)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al arcocoseno de los elementos de la valarray de entrada.|
|[asin](../standard-library/valarray-functions.md#asin)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al arcoseno de los elementos de la valarray de entrada.|
|[atan](../standard-library/valarray-functions.md#atan)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al principal valor del arcotangente de los elementos de la valarray de entrada.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Devuelve una valarray cuyos elementos son iguales al arcotangente de los componentes cartesianos especificados por una combinación de constantes y elementos de valarrays.|
|[begin](../standard-library/valarray-functions.md#begin)||
|[cos](../standard-library/valarray-functions.md#cos)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al coseno de los elementos de la valarray de entrada.|
|[cosh](../standard-library/valarray-functions.md#cosh)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al coseno hiperbólico de los elementos de la valarray de entrada.|
|[end](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al exponencial natural de los elementos de la valarray de entrada.|
|[log](../standard-library/valarray-functions.md#log)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al logaritmo natural de los elementos de la valarray de entrada.|
|[log10](../standard-library/valarray-functions.md#log10)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al logaritmo común o de base 10 de los elementos de la valarray de entrada.|
|[pow](../standard-library/valarray-functions.md#pow)|Opera en los elementos de constantes y valarrays de entrada, devolviendo una valarray cuyos elementos son iguales a una base especificada mediante los elementos de una valarray de entrada o constante elevada a un exponente especificado por los elementos de una valarray de entrada o una constante.|
|[sin](../standard-library/valarray-functions.md#sin)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al seno de los elementos de la valarray de entrada.|
|[sinh](../standard-library/valarray-functions.md#sinh)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al seno hiperbólico de los elementos de la valarray de entrada.|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales a la raíz cuadrada de los elementos de la valarray de entrada.|
|[swap](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales a la tangente de los elementos de la valarray de entrada.|
|[tanh](../standard-library/valarray-functions.md#tanh)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales a la tangente hiperbólica de los elementos de la valarray de entrada.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Comprueba si los elementos correspondientes de dos valarrays de igual tamaño no son iguales o si todos los elementos de una valarray no son iguales a un valor especificado del tipo de elemento de la valarray.|
|[operator%](../standard-library/valarray-operators.md#op_mod)|Obtiene el resto de dividir los elementos correspondientes de dos valarrays de igual tamaño o de dividir una valarray por un valor especificado del tipo de elemento de la valarray o de dividir un valor especificado por una valarray.|
|[operator&](../standard-library/valarray-operators.md#op_amp)|Obtiene el `AND` bit a bit entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.|
|[operator&&](../standard-library/valarray-operators.md#op_amp_amp)|Obtiene el `AND` lógico entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de valarray.|
|[operator>](../standard-library/valarray-operators.md#op_gt)|Comprueba si los elementos de una valarray son mayores que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o menores que un valor especificado del tipo de elemento de la valarray.|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Comprueba si los elementos de una valarray son mayores o iguales que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o iguales o menores que un valor especificado.|
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|Desplaza hacia la derecha los bits de cada elemento de una valarray un número especificado de posiciones o una cantidad de elementos especificada por una segunda valarray.|
|[operator<](../standard-library/valarray-operators.md#op_lt)|Comprueba si los elementos de una valarray son menores que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o menores que un valor especificado.|
|[operator<=](../standard-library/valarray-operators.md#op_lt_eq)|Comprueba si los elementos de una valarray son menores o iguales que los elementos de una valarray de igual tamaño, o si todos los elementos de una valarray son mayores, iguales o menores que un valor especificado.|
|[operator<<](../standard-library/valarray-operators.md#op_lt_lt)|Desplaza hacia la izquierda los bits de cada elemento de una valarray un número especificado de posiciones o una cantidad de elementos especificada por una segunda valarray.|
|[operator*](../standard-library/valarray-operators.md#op_star)|Obtiene el producto de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|
|[operator+](../standard-library/valarray-operators.md#op_add)|Obtiene la suma de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|
|[operator-](../standard-library/valarray-operators.md#operator-)|Obtiene la diferencia de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|
|[operator/](../standard-library/valarray-operators.md#op_div)|Obtiene el cociente de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|Comprueba si los elementos correspondientes de dos valarrays de igual tamaño son iguales o si todos los elementos de una valarray son iguales a un valor especificado del tipo de elemento de la valarray.|
|[operator^](../standard-library/valarray-operators.md#op_xor)|Obtiene el `OR` exclusivo bit a bit entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|Obtiene el `OR` bit a bit entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|Obtiene el `OR` lógico entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de valarray.|

### <a name="classes"></a>Clases

|||
|-|-|
|[gslice (Clase)](../standard-library/gslice-class.md)|Clase de utilidad para valarray que se usa para definir segmentos multidimensionales de una valarray.|
|[gslice_array (Clase)](../standard-library/gslice-array-class.md)|Una plantilla de clase auxiliar interna que admite objetos de segmentos generales proporcionando operaciones entre matrices de subconjuntos definidas por el segmento general de un valarray.|
|[indirect_array (Clase)](../standard-library/indirect-array-class.md)|Una plantilla de clase auxiliar interna que admite objetos que son subconjuntos de valarrays proporcionando operaciones entre matrices de subconjuntos definidas especificando un subconjunto de índices de una valarray primaria.|
|[mask_array (Clase)](../standard-library/mask-array-class.md)|Una plantilla de clase auxiliar interna que admite objetos que son subconjuntos de valarrays principales, especificados con una expresión booleana, proporcionando operaciones entre las matrices de subconjuntos.|
|[slice (Clase)](../standard-library/slice-class.md)|Clase de utilidad para valarray que se usa para definir subconjuntos unidimensionales de tipo vector de una valarray.|
|[slice_array (Clase)](../standard-library/slice-array-class.md)|Una plantilla de clase auxiliar interna que admite objetos de sector proporcionando operaciones entre matrices de subconjuntos definidas por el segmento de una valarray.|
|[valarray (Clase)](../standard-library/valarray-class.md)|La plantilla de clase describe un objeto que controla una secuencia de elementos de tipo `Type` que se almacenan como una matriz y se diseñan para realizar operaciones matemáticas de alta velocidad, optimizadas para el rendimiento computacional.|

### <a name="specializations"></a>Especializaciones

|||
|-|-|
|[valarray\<bool> (clase)](../standard-library/valarray-bool-class.md)|Una versión especializada de la plantilla de clase valarray \<**tipo**> a elementos de tipo **bool**.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
