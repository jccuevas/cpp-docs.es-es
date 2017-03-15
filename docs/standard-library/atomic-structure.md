---
title: atomic (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 03665af409892b087bcc8a0858513f1f96f0c41d
ms.lasthandoff: 02/24/2017

---
# <a name="atomic-structure"></a>atomic (Estructura)
Describe un objeto que realiza operaciones atómicas sobre un valor almacenado de tipo `Ty`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct atomic;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[atomic::atomic (Constructor)](http://msdn.microsoft.com/Library/a538c43f-4d48-4308-ae1b-bab1839bccb8)|Construye un objeto atómico.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[atomic::operator Ty (Operador)](http://msdn.microsoft.com/Library/a366c700-c7a0-4bcb-8eb4-4b57dfaea065)|Lee y devuelve el valor almacenado. ([atomic::load (Método)](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1))|  
|[atomic::operator= (Operador)](http://msdn.microsoft.com/Library/fe161d57-47ae-4bad-92bf-ce32ac8d5953)|Utiliza un valor especificado para reemplazar el valor almacenado. ([atomic::store (Método)](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b))|  
|[atomic::operator++ (Operador)](http://msdn.microsoft.com/Library/492959e9-1ea8-4e02-a031-82b1b92e91a0)|Incrementa el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator+= (Operador)](http://msdn.microsoft.com/Library/9ec97aa2-c9d7-436b-943d-2989eb2617dd)|Suma un valor especificado al valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator-- (Operador)](http://msdn.microsoft.com/Library/ad7c1ea7-1f6d-4a54-bf26-07630f749864)|Disminuye el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator-= (Operador)](http://msdn.microsoft.com/Library/902d0d9f-88fd-4500-aa2d-1e50f443e77c)|Resta un valor especificado del valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator&= (Operador)](http://msdn.microsoft.com/Library/90e730ac-12e1-4abb-98f5-4eadd6861a89)|Realiza una operación `and` bit a bit sobre un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|  
|[atomic::operator&#124;= (Operador)](http://msdn.microsoft.com/Library/f105eacc-31a6-4906-abba-f1cf013599b2)|Realiza una operación `or` bit a bit sobre un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|  
|[atomic::operator^= (Operador)](http://msdn.microsoft.com/Library/f2a4da9d-67e8-4249-9161-9998e72a33c2)|Realiza una operación `exclusive or` bit a bit sobre un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[atomic::compare_exchange_strong (Método)](http://msdn.microsoft.com/Library/47bbf894-b28c-4ece-959e-67b3863cf4ed)|Realiza una operación `atomic_compare_and_exchange` sobre `this` y devuelve el resultado.|  
|[atomic::compare_exchange_weak (Método)](http://msdn.microsoft.com/Library/e15e421a-f7a3-4272-993a-f487d2242e4f)|Realiza una operación `weak_atomic_compare_and_exchange` sobre `this` y devuelve el resultado.|  
|[atomic::fetch_add (Método)](http://msdn.microsoft.com/Library/c68b91f2-6e8a-4ffa-8991-6bb6d466e1f3)|Suma un valor especificado al valor almacenado.|  
|[atomic::fetch_and (Método)](http://msdn.microsoft.com/Library/a9c83001-b72c-4085-9640-f63f866714b9)|Realiza una operación `and` bit a bit sobre un valor especificado y el valor almacenado.|  
|[atomic::fetch_or (Método)](http://msdn.microsoft.com/Library/4c532f7f-80c5-432a-b34b-48feacab8dca)|Realiza una operación `or` bit a bit sobre un valor especificado y el valor almacenado.|  
|[atomic::fetch_sub (Método)](http://msdn.microsoft.com/Library/8cc80d4b-0942-45a3-9db8-bbf339a903e4)|Resta un valor especificado del valor almacenado.|  
|[atomic::fetch_xor (Método)](http://msdn.microsoft.com/Library/92bbaff8-ee29-4a1e-aee4-d9d405285bfe)|Realiza una operación `exclusive or` bit a bit sobre un valor especificado y el valor almacenado.|  
|[atomic::is_lock_free (Método)](http://msdn.microsoft.com/Library/b99d5130-cdda-40a2-b14c-152b13a8ba45)|Especifica si las operaciones atómicas sobre `this` *no tienen bloqueos*. Un tipo atómico *no tiene bloqueos* si ninguna operación atómica sobre ese tipo emplea bloqueos.|  
|[atomic::load (Método)](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1)|Lee y devuelve el valor almacenado.|  
|[atomic::store (Método)](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b)|Utiliza un valor especificado para reemplazar el valor almacenado.|  
  
## <a name="remarks"></a>Comentarios  
 El tipo `Ty` se debe *poder copiar de forma trivial*. Es decir, el uso de [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) para copiar sus bytes debe generar un objeto `Ty` válido que sea igual que el objeto original. Las funciones miembro `compare_exchange_weak` y `compare_exchange_strong` usan [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) para determinar si dos valores `Ty` son iguales. Estas funciones no utilizarán un `Ty` definido por `operator==`. Las funciones miembro de `atomic` utilizan `memcpy` para copiar valores de tipo `Ty`.  
  
 Existe una especialización parcial, `atomic<Ty *>`, para todos los tipos de puntero. La especialización permite sumar un desplazamiento al valor del puntero administrado o restar un desplazamiento del mismo. Las operaciones aritméticas toman un argumento de tipo `ptrdiff_t` y ajustan ese argumento según el tamaño de `Ty` para que sea coherente con la aritmética normal de dirección.  
  
 Existe una especialización para cada tipo entero excepto `bool`. Cada especialización proporciona un conjunto completo de métodos para operaciones aritméticas y lógicas atómicas.  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 Las especializaciones de entero se derivan de los tipos `atomic_``integral` correspondientes. Por ejemplo, `atomic<unsigned int>` se deriva de `atomic_uint`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atomic  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<atomic>](../standard-library/atomic.md)   
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)




