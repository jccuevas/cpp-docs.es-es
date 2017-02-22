---
title: "&lt; subproceso &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<thread>"
dev_langs: 
  - "C++"
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt; subproceso &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado estándar \< subproceso> para definir la clase `thread` y diversas funciones auxiliares.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En el código compilado mediante **/CLR** o **/clr: pure**, este encabezado está bloqueado.  
  
 El `__STDCPP_THREADS__` macro se define como un valor distinto de cero para indicar que los subprocesos son compatibles con este encabezado.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-classes"></a>Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[Thread (clase)](../standard-library/thread-class.md)|Define un objeto que se utiliza para observar y administrar un subproceso de ejecución en una aplicación.|  
  
### <a name="public-structures"></a>Estructuras públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[hash (estructura, STL)](../standard-library/hash-structure-stl.md)|Define una función miembro que devuelve un valor que se determina de forma única mediante un `thread::id`. Define la función miembro un [hash](hash%20Class.md) función que es adecuado para los valores de asignación de tipo `thread::id` a una distribución de valores de índice.|  
  
### <a name="public-functions"></a>Funciones públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[get_id (función)](../Topic/%3Cthread%3E%20functions.md#get_id_function)|Identifica de forma única el subproceso de ejecución actual.|  
|[sleep_for (función)](../Topic/%3Cthread%3E%20functions.md#sleep_for_function)|Bloquea el subproceso que realiza la llamada.|  
|[sleep_until (función)](../Topic/%3Cthread%3E%20functions.md#sleep_until_function)|Bloquea el subproceso que realiza la llamada al menos hasta la hora especificada.|  
|[swap (función)](../Topic/%3Cthread%3E%20functions.md#swap_function)|Intercambia los Estados de dos `thread` objetos.|  
|[yield (función)](../Topic/%3Cthread%3E%20functions.md#yield_function)|Indica el sistema operativo para ejecutar otros subprocesos, incluso si el subproceso actual normalmente seguirán ejecutándose.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador > = (operador)](../Topic/%3Cthread%3E%20operators.md#operator_gt__eq)|Determina si un `thread::id` objeto es mayor o igual que otro.|  
|[operador > (operador)](../Topic/%3Cthread%3E%20operators.md#operator_gt_)|Determina si un `thread::id` es mayor que otro objeto.|  
|[operador < = (operador)](../Topic/%3Cthread%3E%20operators.md#operator_lt__eq)|Determina si un `thread::id` objeto es menor o igual a otro.|  
|[operador < (operador)](../Topic/%3Cthread%3E%20operators.md#operator_lt_)|Determina si un `thread::id` objeto es menor que otro.|  
|[operador! = (operador)](../Topic/%3Cthread%3E%20operators.md#operator_neq)|Compara dos objetos `thread::id` para determinar si no son iguales.|  
|[Operator == (operador)](../Topic/%3Cthread%3E%20operators.md#operator_eq_eq)|Compara dos objetos `thread::id` para determinar si son iguales.|  
|[operador << (operador)](../Topic/%3Cthread%3E%20operators.md#operator_lt__lt_)|Inserta una representación de texto de un `thread::id` objeto en una secuencia.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

