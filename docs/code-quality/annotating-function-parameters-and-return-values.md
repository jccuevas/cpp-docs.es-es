---
title: Annotar parámetros de función y valores devueltos
description: Guía de referencia para el parámetro de función y las anotaciones de valor devuelto.
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: c787dcfb252da1abe47251d66c46689db289cf15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328008"
---
# <a name="annotating-function-parameters-and-return-values"></a>Annotar parámetros de función y valores devueltos

En este artículo se describen los usos típicos de anotaciones para parámetros de función simples (escalares y punteros a estructuras y clases) y la mayoría de los tipos de búferes. En este artículo también se muestran patrones de uso comunes para anotaciones. Para obtener anotaciones adicionales relacionadas con funciones, vea [Anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Parámetros del puntero

Para las anotaciones de la tabla siguiente, cuando se anota un parámetro de puntero, el analizador notifica un error si el puntero es null. Esta anotación se aplica a los punteros y a cualquier elemento de datos al que se señale.

### <a name="annotations-and-descriptions"></a>Anotaciones y descripciones

- `_In_`

     Anota parámetros de entrada que son escalares, estructuras, punteros a estructuras y similares. Se puede utilizar explícitamente en escalares simples. El parámetro debe ser válido en estado previo y no se modificará.

- `_Out_`

     Anota parámetros de salida que son escalares, estructuras, punteros a estructuras y similares. No aplique esta anotación a un objeto que no pueda devolver un valor, por ejemplo, un escalar que se pasa por valor. El parámetro no tiene que ser válido en estado previo, pero debe ser válido en estado posterior.

- `_Inout_`

     Anota un parámetro que la función cambiará. Debe ser válido en estado previo y post-estado, pero se supone que tiene valores diferentes antes y después de la llamada. Debe aplicarse a un valor modificable.

- `_In_z_`

     Puntero a una cadena terminada en null que se usa como entrada. La cadena debe ser válida en estado previo. Se `PSTR`prefieren las variantes de , que ya tienen las anotaciones correctas.

- `_Inout_z_`

     Puntero a una matriz de caracteres terminada en null que se modificará. Debe ser válido antes y después de la llamada, pero se supone que el valor ha cambiado. Se puede mover el terminador nulo, pero solo se puede tener acceso a los elementos hasta el terminador nulo original.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Puntero a una matriz, que la función lee. La matriz es `s` de elementos de tamaño, todos los cuales deben ser válidos.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Utilice esta variante solo cuando el tamaño no se pueda expresar como elementos. Por ejemplo, `char` las `_bytes_` cadenas usarían la variante `wchar_t` solo si lo haría una función similar que utiliza.

- `_In_reads_z_(s)`

     Puntero a una matriz que está terminada en null y tiene un tamaño conocido. Los elementos hasta el `s` terminador nulo, o si no hay un terminador nulo, deben ser válidos en estado previo. Si el tamaño se conoce `s` en bytes, escale por el tamaño del elemento.

- `_In_reads_or_z_(s)`

     Puntero a una matriz que está terminada en null o tiene un tamaño conocido, o ambos. Los elementos hasta el `s` terminador nulo, o si no hay un terminador nulo, deben ser válidos en estado previo. Si el tamaño se conoce `s` en bytes, escale por el tamaño del elemento. (Utilizado para `strn` la familia.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Puntero a una `s` matriz de elementos (resp. bytes) que escribirá la función. Los elementos de matriz no tienen que ser válidos en estado previo y el número de elementos que son válidos en estado posterior no se especifica. Si hay anotaciones en el tipo de parámetro, se aplican en estado posterior. Por ejemplo, considere el fragmento de código siguiente:

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     En este ejemplo, el llamador proporciona un búfer de `size` elementos para `p1`. `MyStringCopy`hace que algunos de esos elementos sean válidos. Lo que es `_Null_terminated_` más `PWSTR` importante, la anotación en significa que `p1` se termina en null en estado posterior. De este modo, el número de elementos válidos sigue estando bien definido, pero no se requiere un recuento de elementos específico.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Utilice esta variante solo cuando el tamaño no se pueda expresar como elementos. Por ejemplo, `char` las `_bytes_` cadenas usarían la variante `wchar_t` solo si lo haría una función similar que utiliza.

- `_Out_writes_z_(s)`

     Un puntero a `s` una matriz de elementos. Los elementos no tienen que ser válidos en estado previo. En el estado posterior, los elementos a través del terminador nulo, que debe estar presente, deben ser válidos. Si el tamaño se conoce `s` en bytes, escale por el tamaño del elemento.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Puntero a una matriz, que se lee y escribe en la función. Es de elementos de tamaño `s` y válido en estado previo y post-estado.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Utilice esta variante solo cuando el tamaño no se pueda expresar como elementos. Por ejemplo, `char` las `_bytes_` cadenas usarían la variante `wchar_t` solo si lo haría una función similar que utiliza.

- `_Inout_updates_z_(s)`

     Puntero a una matriz terminada en null y tiene un tamaño conocido. Los elementos a través del terminador nulo, que debe estar presente, deben ser válidos tanto en estado previo como en estado posterior. Se supone que el valor del estado posterior es diferente del valor del estado anterior; que incluye la ubicación del terminador nulo. Si el tamaño se conoce `s` en bytes, escale por el tamaño del elemento.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Un puntero a `s` una matriz de elementos. Los elementos no tienen que ser válidos en estado previo. En el estado posterior, los `c`elementos hasta el -th elemento debe ser válido. La `_bytes_` variante se puede utilizar si el tamaño se conoce en bytes en lugar de en número de elementos.

     Por ejemplo:

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Puntero a una matriz, que la función lee y escribe. Es de elementos de tamaño, `s` todos los cuales deben `c` ser válidos en estado previo y los elementos deben ser válidos en estado posterior.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Utilice esta variante solo cuando el tamaño no se pueda expresar como elementos. Por ejemplo, `char` las `_bytes_` cadenas usarían la variante `wchar_t` solo si lo haría una función similar que utiliza.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Puntero a una matriz, que se lee y `s` escribe mediante la función de elementos size. Definido como equivalente a:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     En otras palabras, todos los elementos `s` que existen en el búfer hasta en el estado anterior son válidos en el estado previo y posterior.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de elementos. Utilice esta variante solo cuando el tamaño no se pueda expresar como elementos. Por ejemplo, `char` las `_bytes_` cadenas usarían la variante `wchar_t` solo si lo haría una función similar que utiliza.

- `_In_reads_to_ptr_(p)`

     Un puntero a una `p - _Curr_` matriz para `p` `_Curr_`la que (es decir, menos) es una expresión válida. Los elementos anteriores `p` deben ser válidos en estado previo.

    Por ejemplo:

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Puntero a una matriz terminada en `p - _Curr_` null para `p` la `_Curr_`que expresión (es decir, menos ) es una expresión válida. Los elementos anteriores `p` deben ser válidos en estado previo.

- `_Out_writes_to_ptr_(p)`

     Un puntero a una `p - _Curr_` matriz para `p` `_Curr_`la que (es decir, menos) es una expresión válida. Los elementos anteriores `p` no tienen que ser válidos en estado previo y deben ser válidos en estado posterior.

- `_Out_writes_to_ptr_z_(p)`

     Un puntero a una matriz terminada `p - _Curr_` en null `p` `_Curr_`para la que (es decir, menos) es una expresión válida. Los elementos anteriores `p` no tienen que ser válidos en estado previo y deben ser válidos en estado posterior.

## <a name="optional-pointer-parameters"></a>Parámetros de puntero opcionales

Cuando una anotación `_opt_`de parámetro de puntero incluye , indica que el parámetro puede ser null. De lo contrario, la anotación se comporta igual `_opt_`que la versión que no incluye . Aquí está una `_opt_` lista de las variantes de las anotaciones del parámetro de puntero:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Parámetros del puntero de salida

Los parámetros del puntero de salida requieren una notación especial para desambiguar la nulidad en el parámetro y la ubicación señalada.

### <a name="annotations-and-descriptions"></a>Anotaciones y descripciones

- `_Outptr_`

   El parámetro no puede ser null y en el estado posterior la ubicación señalada no puede ser null y debe ser válida.

- `_Outptr_opt_`

   El parámetro puede ser null, pero en el estado posterior la ubicación señalada no puede ser null y debe ser válida.

- `_Outptr_result_maybenull_`

   El parámetro no puede ser null y en el estado posterior la ubicación señalada puede ser null.

- `_Outptr_opt_result_maybenull_`

   El parámetro puede ser null y, en el estado posterior, la ubicación señalada puede ser null.

  En la tabla siguiente, se insertan subcadenas adicionales en el nombre de anotación para calificar aún más el significado de la anotación. Las distintas `_z`subcadenas `_buffer_` `_bytebuffer_`son `_to_`, `_COM_`, , , y .

> [!IMPORTANT]
> Si la interfaz que está anotando es COM, utilice el formulario COM de estas anotaciones. No utilice las anotaciones COM con ninguna otra interfaz de tipo.

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   El puntero devuelto `_Null_terminated_` tiene la anotación.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   El puntero devuelto tiene semántica COM y, por lo tanto, lleva una `_On_failure_` condición posterior a que el puntero devuelto es null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   El puntero devuelto apunta a `s` un búfer válido de elementos de tamaño o bytes.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   El puntero devuelto apunta a `s` un búfer de elementos de tamaño o bytes, de los cuales los primeros `c` son válidos.

Ciertas convenciones de interfaz suponen que los parámetros de salida se anulan en caso de error. Excepto para el código COM explícitamente, se prefieren los formularios de la tabla siguiente. Para el código COM, use los formularios COM correspondientes que se enumeran en la sección anterior.

- `_Result_nullonfailure_`

   Modifica otras anotaciones. El resultado se establece en null si se produce un error en la función.

- `_Result_zeroonfailure_`

   Modifica otras anotaciones. El resultado se establece en cero si se produce un error en la función.

- `_Outptr_result_nullonfailure_`

   El puntero devuelto apunta a un búfer válido si la función se realiza correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro no opcional.

- `_Outptr_opt_result_nullonfailure_`

   El puntero devuelto apunta a un búfer válido si la función se realiza correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro opcional.

- `_Outref_result_nullonfailure_`

   El puntero devuelto apunta a un búfer válido si la función se realiza correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro de referencia.

## <a name="output-reference-parameters"></a>Parámetros de referencia de salida

Un uso común del parámetro de referencia es para los parámetros de salida. Para parámetros de `int&`referencia `_Out_` de salida simples como , proporciona la semántica correcta. Sin embargo, cuando el valor `int *&`de salida es `_Outptr_ int **` un puntero como , las anotaciones de puntero equivalentes como no proporcionan la semántica correcta. Para expresar de forma concisa la semántica de los parámetros de referencia de salida para los tipos de puntero, utilice estas anotaciones compuestas:

### <a name="annotations-and-descriptions"></a>Anotaciones y descripciones

- `_Outref_`

     El resultado debe ser válido en estado posterior y no puede ser null.

- `_Outref_result_maybenull_`

     El resultado debe ser válido en el estado posterior, pero puede ser null en el estado posterior.

- `_Outref_result_buffer_(s)`

     El resultado debe ser válido en estado posterior y no puede ser null. Apunta al búfer `s` válido de los elementos de tamaño.

- `_Outref_result_bytebuffer_(s)`

     El resultado debe ser válido en estado posterior y no puede ser null. Apunta al búfer `s` válido de bytes de tamaño.

- `_Outref_result_buffer_to_(s, c)`

     El resultado debe ser válido en estado posterior y no puede ser null. Puntos al `s` búfer de elementos, de los cuales los primeros `c` son válidos.

- `_Outref_result_bytebuffer_to_(s, c)`

     El resultado debe ser válido en estado posterior y no puede ser null. Puntos al `s` búfer de `c` bytes de los cuales los primeros son válidos.

- `_Outref_result_buffer_all_(s)`

     El resultado debe ser válido en estado posterior y no puede ser null. Apunta al búfer `s` válido de elementos válidos de tamaño.

- `_Outref_result_bytebuffer_all_(s)`

     El resultado debe ser válido en estado posterior y no puede ser null. Apunta al búfer `s` válido de bytes de elementos válidos.

- `_Outref_result_buffer_maybenull_(s)`

     El resultado debe ser válido en el estado posterior, pero puede ser null en el estado posterior. Apunta al búfer `s` válido de los elementos de tamaño.

- `_Outref_result_bytebuffer_maybenull_(s)`

     El resultado debe ser válido en el estado posterior, pero puede ser null en el estado posterior. Apunta al búfer `s` válido de bytes de tamaño.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     El resultado debe ser válido en el estado posterior, pero puede ser null en el estado posterior. Puntos al `s` búfer de elementos, de los cuales los primeros `c` son válidos.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     El resultado debe ser válido en el estado posterior, pero puede ser null en el estado posterior. Puntos al `s` búfer de `c` bytes de los cuales los primeros son válidos.

- `_Outref_result_buffer_all_maybenull_(s)`

     El resultado debe ser válido en el estado posterior, pero puede ser null en el estado posterior. Apunta al búfer `s` válido de elementos válidos de tamaño.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     El resultado debe ser válido en el estado posterior, pero puede ser null en el estado posterior. Apunta al búfer `s` válido de bytes de elementos válidos.

## <a name="return-values"></a>Valores devueltos

El valor devuelto de una `_Out_` función se asemeja a un parámetro, pero está en un nivel diferente de desreferenciación y no es tiene que tener en cuenta el concepto del puntero al resultado. Para las siguientes anotaciones, el valor devuelto es el objeto anotado: un escalar, un puntero a una estructura o un puntero a un búfer. Estas anotaciones tienen la misma `_Out_` semántica que la anotación correspondiente.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Formato de parámetros de cadena

- `_Printf_format_string_`Indica que el parámetro es una cadena `printf` de formato para su uso en una expresión.

     **Ejemplo**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`Indica que el parámetro es una cadena `scanf` de formato para su uso en una expresión.

     **Ejemplo**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`Indica que el parámetro es una cadena `scanf_s` de formato para su uso en una expresión.

     **Ejemplo**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Otras anotaciones comunes

### <a name="annotations-and-descriptions"></a>Anotaciones y descripciones

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     El parámetro, campo o resultado está en `low` el `hi`intervalo (incluido) de a . Equivalente `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` a eso se aplica al objeto anotado junto con las condiciones de estado previo o posterior a estado adecuadas.

    > [!IMPORTANT]
    > Aunque los nombres contienen "in" y "out", la semántica de `_In_` y `_Out_` **no** se aplican a estas anotaciones.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     El valor anotado `expr`es exactamente . Equivalente `_Satisfies_(_Curr_ == expr)` a eso se aplica al objeto anotado junto con las condiciones de estado previo o posterior a estado adecuadas.

- `_Struct_size_bytes_(size)`

     Se aplica a una declaración de clase o struct. Indica que un objeto válido de ese tipo puede ser mayor que el `size`tipo declarado, con el número de bytes dado por . Por ejemplo:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     El tamaño del búfer `pM` en `MyStruct *` bytes de un parámetro de tipo se toma como:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Recursos relacionados

[Blog del equipo de análisis de código](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Consulte también

- [Utilizar anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)
