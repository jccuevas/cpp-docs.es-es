---
title: "&lt;atomic&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<atomic>"
  - "atomic/std::atomic_int_least32_t"
  - "atomic/std::atomic_ullong"
  - "atomic/std::atomic_ptrdiff_t"
  - "atomic/std::atomic_char16_t"
  - "atomic/std::atomic_schar"
  - "atomic/std::atomic_ulong"
  - "atomic/std::atomic_uint_fast32_t"
  - "atomic/std::atomic_uint8_t"
  - "atomic/std::atomic_int32_t"
  - "atomic/std::atomic_uint_fast64_t"
  - "atomic/std::atomic_uint32_t"
  - "atomic/std::atomic_int16_t"
  - "atomic/std::atomic_uintmax_t"
  - "atomic/std::atomic_intmax_t"
  - "atomic/std::atomic_long"
  - "atomic/std::atomic_int"
  - "atomic/std::atomic_uint_least8_t"
  - "atomic/std::atomic_size_t"
  - "atomic/std::atomic_uint_fast16_t"
  - "atomic/std::atomic_wchar_t"
  - "atomic/std::atomic_int_fast64_t"
  - "atomic/std::atomic_uint_fast8_t"
  - "atomic/std::atomic_int_fast8_t"
  - "atomic/std::atomic_intptr_t"
  - "atomic/std::atomic_uint"
  - "atomic/std::atomic_uint16_t"
  - "atomic/std::atomic_char32_t"
  - "atomic/std::atomic_uint64_t"
  - "atomic/std::atomic_ushort"
  - "atomic/std::atomic_int_least16_t"
  - "atomic/std::atomic_char"
  - "atomic/std::atomic_uint_least32_t"
  - "atomic/std::atomic_uintptr_t"
  - "atomic/std::atomic_short"
  - "atomic/std::atomic_llong"
  - "atomic/std::atomic_uint_least16_t"
  - "atomic/std::atomic_int_fast16_t"
  - "atomic/std::atomic_int_least8_t"
  - "atomic/std::atomic_int_least64_t"
  - "atomic/std::atomic_int_fast32_t"
  - "atomic/std::atomic_uchar"
  - "atomic/std::atomic_int8_t"
  - "atomic/std::atomic_int64_t"
  - "atomic/std::atomic_uint_least64_t"
dev_langs: 
  - "C++"
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;atomic&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define clases y clases de plantilla para utilizar para crear los tipos que las operaciones atómicas admiten.  
  
## Sintaxis  
  
```cpp  
#include <atomic>  
```  
  
## Comentarios  
  
> [!NOTE]
>  En el código compilado utilizando **\/clr** o **\/clr:pure**, este encabezado está bloqueado.  
  
 Una operación atómica tiene dos propiedades de clave que le ayudan a varios subprocesos de uso correctamente a manipular un objeto sin utilizar la exclusión mutua se bloqueen.  
  
-   Dado que una operación atómica es indivisible, una segunda operación atómica en el mismo objeto desde un subproceso diferente puede obtener el estado de objeto antes o después de la primera operación atómica.  
  
-   Por su argumento de [memory\_order](../Topic/memory_order%20Enum.md) , una operación atómica establece ordenar los requisitos para la visibilidad de los efectos de otras operaciones atómicas en el mismo subproceso.  Por consiguiente, deshabilita las optimizaciones del compilador que cumplen los requisitos de ordenación.  
  
 En algunas plataformas, no sería posible implementar eficazmente las operaciones atómicas para algunos tipos sin utilizar `mutex` bloqueos.  Un tipo atómico es *bloqueo\- libre* si ninguna operaciones atómicas en ese uso de tipo bloqueos.  
  
 La clase [atomic\_flag](../standard-library/atomic-flag-structure.md) proporciona un tipo atómico mínimo que contiene un indicador de `bool` .  Las operaciones son siempre bloqueo\- disponibles.  
  
 La clase de plantilla `atomic<Ty>` almacena un objeto del tipo `Ty` de argumentos y proporciona acceso atómico que valor almacenado.  Puede crear instancias mediante cualquier tipo que se pueden copiar mediante [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) y comprobar la igualdad mediante [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md).  En particular, puede utilizarlo con tipos definidos por el usuario que cumplen estos requisitos y, en muchos casos, con los tipos de punto flotante.  
  
 La plantilla también tiene un conjunto de especializaciones de tipos enteros y de una especialización parcial para punteros.  Estas especializaciones proporcionan operaciones adicionales que no están disponibles a través de la plantilla principal.  
  
## Especializaciones de puntero  
 Especializaciones parciales de `atomic<Ty *>` se aplican a todos los tipos de puntero.  Proporcionan métodos para la aritmética con punteros.  
  
## Especializaciones completas  
 Especializaciones de `atomic<integral>` se aplican a todos los tipos enteros.  Proporcionan operaciones adicionales que no están disponibles a través de la plantilla principal.  
  
 Cada tipo de `atomic<integral>` tiene una macro correspondiente que puede utilizar en `if directive` para determinar en tiempo de compilación si las operaciones en ese tipo son bloqueo\- disponibles.  Si el valor de la macro es cero, las operaciones en el tipo no son bloqueo\- disponibles.  Si el valor es 1, las operaciones podrían ser bloqueo\- libres, y se requiere una comprobación en tiempo de ejecución.  Si el valor es 2, las operaciones son bloqueo\- disponibles.  Puede utilizar la función `atomic_is_lock_free` para determinar en tiempo de ejecución si las operaciones en el tipo son bloqueo\- disponibles.  
  
 Para cada uno de los tipos enteros, hay un tipo atómico denominado correspondiente que administra un objeto de ese tipo entero.  Cada tipo de `atomic_integral` tiene el mismo conjunto de funciones miembro que la instancia correspondiente de `atomic<Ty>` y puede pasarse a funciones atómicas de no un miembro de los.  
  
|Tipo `atomic_integral`.|Tipo entero|macro de`atomic_is_lock_free`|  
|-----------------------------|-----------------|-----------------------------------|  
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
  
 Los nombres de Typedef existen para las especializaciones de plantilla atómica para algunos de los tipos definidos en el encabezado \<inttypes.h.\>  
  
|Tipo atómico|Nombre de Typedef|  
|------------------|-----------------------|  
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
  
## Structs  
  
|Name|Descripción|  
|----------|-----------------|  
|[atomic \(Estructura\)](../standard-library/atomic-structure.md)|Describe un objeto que realiza operaciones atómicas en un valor almacenado.|  
|[atomic\_flag \(Estructura\)](../standard-library/atomic-flag-structure.md)|Describe un objeto que establece y borra una marca `bool` de forma atómica.|  
  
## Enumeraciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[memory\_order \(Enum\)](../Topic/memory_order%20Enum.md)|Proporciona nombres simbólicos para las operaciones de sincronización en ubicaciones de memoria.  Estas operaciones afectan a cómo las asignaciones de un subproceso se hacen visibles en otro.|  
  
## Funciones  
 En la lista siguiente, funciones que no finalizan en `_explicit` tienen la semántica de `_explicit`correspondiente, salvo que las tienen los argumentos implícitos de [memory\_order](../Topic/memory_order%20Enum.md) de `memory_order_seq_cst`.  
  
|Name|Descripción|  
|----------|-----------------|  
|[atomic\_compare\_exchange\_strong \(Función\)](../Topic/atomic_compare_exchange_strong%20Function.md)|Realiza una operación *atómica de comparación e intercambio*.|  
|[atomic\_compare\_exchange\_strong\_explicit \(Función\)](../Topic/atomic_compare_exchange_strong_explicit%20Function.md)|Realiza una operación *atómica de comparación e intercambio*.|  
|[atomic\_compare\_exchange\_weak \(Función\)](../Topic/atomic_compare_exchange_weak%20Function.md)|Realiza una operación *atómica débil de comparación e intercambio*.|  
|[atomic\_compare\_exchange\_weak\_explicit \(Función\)](../Topic/atomic_compare_exchange_weak_explicit%20Function.md)|Realiza una operación *atómica débil de comparación e intercambio*.|  
|[atomic\_exchange \(Función\)](../Topic/atomic_exchange%20Function.md)|Reemplaza un valor almacenado.|  
|[atomic\_exchange\_explicit \(Función\)](../Topic/atomic_exchange_explicit%20Function.md)|Reemplaza un valor almacenado.|  
|[atomic\_fetch\_add \(Función\)](../Topic/atomic_fetch_add%20Function.md)|Agrega un valor especificado con el valor almacenado existente.|  
|[atomic\_fetch\_add\_explicit \(Función\)](../Topic/atomic_fetch_add_explicit%20Function.md)|Agrega un valor especificado con el valor almacenado existente.|  
|[atomic\_fetch\_and \(Función\)](../Topic/atomic_fetch_and%20Function.md)|Realiza `and` bit a bit en un valor especificado y un valor almacenado existente.|  
|[atomic\_fetch\_and\_explicit \(Función\)](../Topic/atomic_fetch_and_explicit%20Function.md)|Realiza `and` bit a bit en un valor especificado y un valor almacenado existente.|  
|[atomic\_fetch\_or \(Función\)](../Topic/atomic_fetch_or%20Function.md)|Realiza `or` bit a bit en un valor especificado y un valor almacenado existente.|  
|[atomic\_fetch\_or\_explicit \(Función\)](../Topic/atomic_fetch_or_explicit%20Function.md)|Realiza `or` bit a bit en un valor especificado y un valor almacenado existente.|  
|[atomic\_fetch\_sub \(Función\)](../Topic/atomic_fetch_sub%20Function.md)|Resta un valor especificado de un valor almacenado existente.|  
|[atomic\_fetch\_sub\_explicit \(Función\)](../Topic/atomic_fetch_sub_explicit%20Function.md)|Resta un valor especificado de un valor almacenado existente.|  
|[atomic\_fetch\_xor \(Función\)](../Topic/atomic_fetch_xor%20Function.md)|Realiza `exclusive or` bit a bit en un valor especificado y un valor almacenado existente.|  
|[atomic\_fetch\_xor\_explicit \(Función\)](../Topic/atomic_fetch_xor_explicit%20Function.md)|Realiza `exclusive or` bit a bit en un valor especificado y un valor almacenado existente.|  
|[atomic\_flag\_clear \(Función\)](../Topic/atomic_flag_clear%20Function.md)|Establece la marca en un objeto de `atomic_flag` a `false`.|  
|[atomic\_flag\_clear\_explicit \(Función\)](../Topic/atomic_flag_clear_explicit%20Function.md)|Establece la marca en un objeto de `atomic_flag` a `false`.|  
|[atomic\_flag\_test\_and\_set \(Función\)](../Topic/atomic_flag_test_and_set%20Function.md)|Establece la marca en un objeto de `atomic_flag` a `true`.|  
|[atomic\_flag\_test\_and\_set\_explicit \(Función\)](../Topic/atomic_flag_test_and_set_explicit%20Function.md)|Establece la marca en un objeto de `atomic_flag` a `true`.|  
|[atomic\_init \(Función\)](../Topic/atomic_init%20Function.md)|Establece el valor almacenado en un objeto de `atomic` .|  
|[atomic\_is\_lock\_free \(Función\)](../Topic/atomic_is_lock_free%20Function.md)|Especifica si las operaciones atómicas en un objeto especificado son bloqueo\- disponibles.|  
|[atomic\_load \(Función\)](../Topic/atomic_load%20Function.md)|Atómico recupera un valor.|  
|[atomic\_load\_explicit \(Función\)](../Topic/atomic_load_explicit%20Function.md)|Atómico recupera un valor.|  
|[atomic\_signal\_fence \(Función\)](../Topic/atomic_signal_fence%20Function.md)|Actúa como *barrera* que establezca la memoria que solicita requisitos entre las barreras en un subproceso de la llamada que tiene los controladores señalado ejecutados en el mismo subproceso.|  
|[atomic\_store \(Función\)](../Topic/atomic_store%20Function.md)|Atómico almacena un valor.|  
|[atomic\_store\_explicit \(Función\)](../Topic/atomic_store_explicit%20Function.md)|Atómico almacena un valor.|  
|[atomic\_thread\_fence \(Función\)](../Topic/atomic_thread_fence%20Function.md)|Actúa como *barrera* que establezca la memoria que solicita requisitos con respecto a otras barreras.|  
|[kill\_dependency \(Función\)](../Topic/kill_dependency%20Function.md)|Divide una cadena posible de la dependencia.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)