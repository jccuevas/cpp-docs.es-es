---
title: '&lt;atomic&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
dev_langs:
- C++
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd543003e7edba4e1766efc11670fd6e505820bb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;
Define las clases y las clases de plantilla que se van a usar para crear tipos que admitan operaciones atómicas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <atomic>  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En el código compilado mediante **/CLR**, este encabezado está bloqueado.  
  
 Una operación atómica tiene dos propiedades clave que ayudan a usar varios subprocesos para manipular correctamente un objeto sin emplear bloqueos de exclusión mutua.  
  
-   Dado que una operación atómica es indivisible, una segunda operación atómica sobre el mismo objeto desde un subproceso diferente puede obtener el estado del objeto únicamente antes o después de la primera operación atómica.  
  
-   Según su argumento [memory_order](../standard-library/atomic-enums.md#memory_order_enum), una operación atómica establece requisitos de ordenación para la visibilidad de los efectos de otras operaciones atómicas del mismo subproceso. Por consiguiente, inhibe las optimizaciones del compilador que infringen los requisitos de ordenación.  
  
 En algunas plataformas no sería posible implementar realmente las operaciones atómicas para algunos tipos sin usar bloqueos `mutex`. Un tipo atómico *no tiene bloqueos* si ninguna operación atómica sobre ese tipo emplea bloqueos.  
  
 **C++11**: en los controladores de señal puede realizar operaciones atómicas sobre un objeto `obj` si `obj.is_lock_free()` o `atomic_is_lock_free(x)` son True.  
  
 La clase [atomic_flag](../standard-library/atomic-flag-structure.md) proporciona un tipo atómico mínimo que contiene una marca `bool`. Sus operaciones nunca tienen bloqueos.  
  
 La clase de plantilla `atomic<T>` almacena un objeto de su tipo de argumento `T` y proporciona acceso atómico a ese valor almacenado. Puede crear instancias de ella mediante cualquier tipo que se pueda copiar mediante [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) y cuya igualdad se pueda probar mediante [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md). En concreto, puede usarla con tipos definidos por el usuario que cumplan estos requisitos y, en muchos casos, con tipos de punto flotante.  
  
 La plantilla también tiene un conjunto de especializaciones para tipos enteros y una especialización parcial para punteros. Estas especializaciones proporcionan operaciones adicionales que no están disponibles a través de la plantilla principal.  
  
## <a name="pointer-specializations"></a>Especializaciones de puntero  
 Las especializaciones parciales `atomic<T *>` se aplican a todos los tipos de puntero. Proporcionan métodos para la aritmética de puntero.  
  
## <a name="integral-specializations"></a>Especializaciones de entero  
 Las especializaciones `atomic<integral>` se aplican a todos los tipos enteros. Proporcionan operaciones adicionales que no están disponibles a través de la plantilla principal.  
  
 Cada tipo `atomic<integral>` tiene una macro correspondiente que se puede usar en `if directive` para determinar en tiempo de compilación si las operaciones de ese tipo tienen bloqueos o no. Si el valor de la macro es cero, las operaciones del tipo tienen bloqueos. Si el valor es 1, las operaciones pueden no tener bloqueos y se necesita una comprobación en tiempo de ejecución. Si el valor es 2, las operaciones no tienen bloqueos. Puede usar la función `atomic_is_lock_free` para determinar en tiempo de ejecución si las operaciones sobre el tipo tienen bloqueos o no.  
  
 Hay un tipo atómico con nombre correspondiente para cada uno de los tipos enteros que administra un objeto de ese tipo entero. Cada tipo `atomic_integral` tiene el mismo conjunto de funciones miembro que la instancia correspondiente de `atomic<T>` y se puede pasar a cualquiera de las funciones atómicas no miembro.  
  
|Tipo `atomic_integral`.|Tipo entero|Macro `atomic_is_lock_free`|  
|----------------------------|-------------------|---------------------------------|  
|`atomic_char`|`char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_schar`|`signed char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_uchar`|`unsigned char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_char16_t`|`char16_t`|`ATOMIC_CHAR16_T_LOCK_FREE`|  
|`atomic_char32_t`|`char32_t`|`ATOMIC_CHAR32_T_LOCK_FREE`|  
|`atomic_wchar_t`|`wchar_t`|`ATOMIC_WCHAR_T_LOCK_FREE`|  
|`atomic_short`|`short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_ushort`|`unsigned short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_int`|`int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_uint`|`unsigned int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_long`|`long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_ulong`|`unsigned long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_llong`|`long long`|`ATOMIC_LLONG_LOCK_FREE`|  
|`atomic_ullong`|`unsigned long long`|`ATOMIC_LLONG_LOCK_FREE`|  
  
 Existen nombres de typedef para especializaciones de la plantilla atómica para algunos de los tipos definidos en el encabezado \<inttypes.h>.  
  
|Tipo atómico|Nombre de typedef|  
|-----------------|------------------|  
|`atomic_int8_t`|`atomic<int8_t>`|  
|`atomic_uint8_t`|`atomic<uint8_t>`|  
|`atomic_int16_t`|`atomic<int16_t>`|  
|`atomic_uint16_t`|`atomic<uint16_t>`|  
|`atomic_int32_t`|`atomic<int32_t>`|  
|`atomic_uint32_t`|`atomic<uint32_t>`|  
|`atomic_int64_t`|`atomic<int64_t>`|  
|`atomic_uint64_t`|`atomic<uint64_t>`|  
|`atomic_int_least8_t`|`atomic<int_least8_t>`|  
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|  
|`atomic_int_least16_t`|`atomic<int_least16_t>`|  
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|  
|`atomic_int_least32_t`|`atomic<int_least32_t>`|  
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|  
|`atomic_int_least64_t`|`atomic<int_least64_t>`|  
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|  
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|  
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|  
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|  
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|  
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|  
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|  
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|  
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|  
|`atomic_intptr_t`|`atomic<intptr_t>`|  
|`atomic_uintptr_t`|`atomic<uintptr_t>`|  
|`atomic_size_t`|`atomic<size_t>`|  
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|  
|`atomic_intmax_t`|`atomic<intmax_t>`|  
|`atomic_uintmax_t`|`atomic<uintmax_t>`|  
  
## <a name="structs"></a>Estructuras  
  
|nombre|Descripción|  
|----------|-----------------|  
|[atomic (Estructura)](../standard-library/atomic-structure.md)|Describe un objeto que realiza operaciones atómicas sobre un valor almacenado.|  
|[atomic_flag (Estructura)](../standard-library/atomic-flag-structure.md)|Describe un objeto que establece y borra una marca `bool` de forma atómica.|  
  
## <a name="enums"></a>Enumeraciones  
  
|nombre|Descripción|  
|----------|-----------------|  
|[memory_order (Enumeración)](../standard-library/atomic-enums.md#memory_order_enum)|Proporciona nombres simbólicos para las operaciones de sincronización en ubicaciones de memoria. Estas operaciones afectan a cómo las asignaciones de un subproceso se hacen visibles en otro.|  
  
## <a name="functions"></a>Funciones  
 En la lista siguiente, las funciones que no terminan en `_explicit` tienen la semántica `_explicit` correspondiente, salvo que tienen los argumentos implícitos [memory_order](../standard-library/atomic-enums.md#memory_order_enum) de `memory_order_seq_cst`.  
  
|nombre|Descripción|  
|----------|-----------------|  
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|Realiza una operación *atómica de comparación e intercambio*.|  
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|Realiza una operación *atómica de comparación e intercambio*.|  
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|Realiza una operación *atómica débil de comparación e intercambio*.|  
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|Realiza una operación *atómica débil de comparación e intercambio*.|  
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|Reemplaza un valor almacenado.|  
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|Reemplaza un valor almacenado.|  
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|Agrega un valor especificado a un valor almacenado existente.|  
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|Agrega un valor especificado a un valor almacenado existente.|  
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|Realiza una operación `and` bit a bit sobre un valor especificado y un valor almacenado existente.|  
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|Realiza una operación `and` bit a bit sobre un valor especificado y un valor almacenado existente.|  
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|Realiza una operación `or` bit a bit sobre un valor especificado y un valor almacenado existente.|  
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|Realiza una operación `or` bit a bit sobre un valor especificado y un valor almacenado existente.|  
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|Resta un valor especificado de un valor almacenado existente.|  
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|Resta un valor especificado de un valor almacenado existente.|  
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|Realiza una operación `exclusive or` bit a bit sobre un valor especificado y un valor almacenado existente.|  
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|Realiza una operación `exclusive or` bit a bit sobre un valor especificado y un valor almacenado existente.|  
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|Establece la marca de un objeto `atomic_flag` en `false`.|  
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|Establece la marca de un objeto `atomic_flag` en `false`.|  
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|Establece la marca de un objeto `atomic_flag` en `true`.|  
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|Establece la marca de un objeto `atomic_flag` en `true`.|  
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|Establece el valor almacenado en un objeto `atomic`.|  
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|Especifica si las operaciones atómicas sobre un objeto especificado no tienen bloqueos.|  
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|Recupera de forma atómica un valor.|  
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|Recupera de forma atómica un valor.|  
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|Actúa como una *barrera* que establece requisitos de ordenación de memoria entre barreras de un subproceso que llama cuyos controladores de señal se ejecutan en el mismo subproceso.|  
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|Almacena de forma atómica un valor.|  
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|Almacena de forma atómica un valor.|  
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|Actúa como una *barrera* que establece requisitos de ordenación de memoria con respecto a otras barreras.|  
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|Rompe una posible cadena de dependencia.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)





