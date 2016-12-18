---
title: "atomic (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "atomic/std::atomic"
dev_langs: 
  - "C++"
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atomic (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que realiza operaciones atómicas sobre un valor almacenado de tipo `Ty`.  
  
## Sintaxis  
  
```  
template <class Ty>  
struct atomic;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[atomic::atomic \(Constructor\)](../Topic/atomic::atomic%20Constructor.md)|Construye un objeto atómico.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[atomic::operator Ty \(Operador\)](../Topic/atomic::operator%20Ty%20Operator.md)|Lee y devuelve el valor almacenado. \([atomic::load \(Método\)](../Topic/atomic::load%20Method.md)\)|  
|[atomic::operator\= \(Operador\)](../Topic/atomic::operator=%20Operator.md)|Utiliza un valor especificado para reemplazar el valor almacenado. \([atomic::store \(Método\)](../Topic/atomic::store%20Method.md)\)|  
|||  
|[atomic::operator\+\+ \(Operador\)](../Topic/atomic::operator++%20Operator.md)|Incrementa el valor almacenado.  Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator\+\= \(Operador\)](../Topic/atomic::operator+=%20Operator.md)|Suma un valor especificado al valor almacenado.  Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator\-\- \(Operador\)](../Topic/atomic::operator--%20Operator.md)|Disminuye el valor almacenado.  Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator\-\= \(Operador\)](../Topic/atomic::operator-=%20Operator.md)|Resta un valor especificado del valor almacenado.  Solo lo utilizan las especializaciones de entero y de puntero.|  
|[atomic::operator&\= \(Operador\)](../Topic/atomic::operator&=%20Operator.md)|Realiza una operación `and` bit a bit sobre un valor especificado y el valor almacenado.  Solo lo utilizan las especializaciones de entero.|  
|[atomic::operator&#124;\= \(Operador\)](../Topic/atomic::operator%7C=%20Operator.md)|Realiza una operación `or` bit a bit sobre un valor especificado y el valor almacenado.  Solo lo utilizan las especializaciones de entero.|  
|[atomic::operator^\= \(Operador\)](../Topic/atomic::operator%5E=%20Operator.md)|Realiza una operación `exclusive or` bit a bit sobre un valor especificado y el valor almacenado.  Solo lo utilizan las especializaciones de entero.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[atomic::compare\_exchange\_strong \(Método\)](../Topic/atomic::compare_exchange_strong%20Method.md)|Realiza una operación `atomic_compare_and_exchange` sobre `this` y devuelve el resultado.|  
|[atomic::compare\_exchange\_weak \(Método\)](../Topic/atomic::compare_exchange_weak%20Method.md)|Realiza una operación `weak_atomic_compare_and_exchange` sobre `this` y devuelve el resultado.|  
|[atomic::fetch\_add \(Método\)](../Topic/atomic::fetch_add%20Method.md)|Suma un valor especificado al valor almacenado.|  
|[atomic::fetch\_and \(Método\)](../Topic/atomic::fetch_and%20Method.md)|Realiza una operación `and` bit a bit sobre un valor especificado y el valor almacenado.|  
|[atomic::fetch\_or \(Método\)](../Topic/atomic::fetch_or%20Method.md)|Realiza una operación `or` bit a bit sobre un valor especificado y el valor almacenado.|  
|[atomic::fetch\_sub \(Método\)](../Topic/atomic::fetch_sub%20Method.md)|Resta un valor especificado del valor almacenado.|  
|[atomic::fetch\_xor \(Método\)](../Topic/atomic::fetch_xor%20Method.md)|Realiza una operación `exclusive or` bit a bit sobre un valor especificado y el valor almacenado.|  
|[atomic::is\_lock\_free \(Método\)](../Topic/atomic::is_lock_free%20Method.md)|Especifica si las operaciones atómicas sobre `this` *no tienen bloqueos*.  Un tipo atómico *no tiene bloqueos* si ninguna operación atómica sobre ese tipo utiliza bloqueos.|  
|[atomic::load \(Método\)](../Topic/atomic::load%20Method.md)|Lee y devuelve el valor almacenado.|  
|[atomic::store \(Método\)](../Topic/atomic::store%20Method.md)|Utiliza un valor especificado para reemplazar el valor almacenado.|  
  
## Comentarios  
 El tipo `Ty` se debe *poder copiar de forma trivial*.  Es decir, si se usa [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) para copiar sus bytes se debe generar un objeto `Ty` válido que se compare como igual que el objeto original.  Las funciones miembro `compare_exchange_weak` y `compare_exchange_strong` utilizan [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) para determinar si dos valores `Ty` son iguales.  Estas funciones no utilizarán un `operator==` definido por `Ty`.  Las funciones miembro de `atomic` utilizan `memcpy` para copiar valores de tipo `Ty`.  
  
 Existe una especialización parcial, `atomic<Ty *>`, para todos los tipos de puntero.  La especialización permite sumar un desplazamiento al valor del puntero administrado o restar un desplazamiento del mismo.  Las operaciones aritméticas toman un argumento de tipo `ptrdiff_t` y ajustan ese argumento según el tamaño de `Ty` para que sea coherente con la aritmética normal de dirección.  
  
 Existe una especialización para cada tipo entero excepto `bool`.  Cada especialización proporciona un conjunto completo de métodos para operaciones aritméticas y lógicas atómicas.  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 Las especializaciones de entero se derivan de los tipos `atomic_``integral` correspondientes.  Por ejemplo, `atomic<unsigned int>` se deriva de `atomic_uint`.  
  
## Requisitos  
 **Encabezado:** atomic  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<atomic\>](../standard-library/atomic.md)   
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)