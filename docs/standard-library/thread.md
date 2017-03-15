---
title: '&lt;subproceso&gt; | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <thread>
dev_langs:
- C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 18
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 9b32de86d2ec84017157cccf1a05b9e9b6802e47
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt"></a>&lt;subproceso&gt;
Incluya el encabezado estándar \<subproceso > para definir la clase `thread` y diversas funciones auxiliares.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En el código que se compila con **/CLR**, este encabezado está bloqueado.  
  
 El `__STDCPP_THREADS__` macro se define como un valor distinto de cero para indicar que los subprocesos son compatibles con este encabezado.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-classes"></a>Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[thread (Clase)](../standard-library/thread-class.md)|Define un objeto que se utiliza para observar y administrar un subproceso de ejecución en una aplicación.|  
  
### <a name="public-structures"></a>Estructuras públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[hash (Estructura, biblioteca estándar de C++)](../standard-library/hash-structure-stl.md)|Define una función miembro que devuelve un valor que se determina de forma exclusiva por un `thread::id`. Define la función miembro un [hash](../standard-library/hash-class.md) (función) que es adecuado para los valores de asignación de tipo `thread::id` a una distribución de valores de índice.|  
  
### <a name="public-functions"></a>Funciones públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[get_id (función)](../standard-library/thread-functions.md#get_id_function)|Identifica de forma única el subproceso de ejecución actual.|  
|[sleep_for (función)](../standard-library/thread-functions.md#sleep_for_function)|Bloquea el subproceso de llamada.|  
|[sleep_until (función)](../standard-library/thread-functions.md#sleep_until_function)|Bloquea el subproceso de llamada al menos hasta la hora especificada.|  
|[swap (Función)](../standard-library/thread-functions.md#swap_function)|Intercambia los Estados de dos `thread` objetos.|  
|[yield (función)](../standard-library/thread-functions.md#yield_function)|Indica al sistema operativo que ejecute otros subprocesos, incluso si el subproceso actual seguiría ejecutándose en condiciones normales.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador > = (operador)](../standard-library/thread-operators.md#operator_gt__eq)|Determina si un objeto `thread::id` es mayor o igual que otro objeto.|  
|[operador > (operador)](../standard-library/thread-operators.md#operator_gt_)|Determina si un objeto `thread::id` es mayor que otro objeto.|  
|[(operador)<=></=>](../standard-library/thread-operators.md#operator_lt__eq)|Determina si un objeto `thread::id` es menor o igual que otro objeto.|  
|[(operador)<>](../standard-library/thread-operators.md#operator_lt_)|Determina si un objeto `thread::id` es menor que otro objeto.|  
|[operador! = (operador)](../standard-library/thread-operators.md#operator_neq)|Compara dos objetos `thread::id` para determinar si no son iguales.|  
|[Operator == (operador)](../standard-library/thread-operators.md#operator_eq_eq)|Compara dos objetos `thread::id` para determinar si son iguales.|  
|[(operador)<>](../standard-library/thread-operators.md#operator_lt__lt_)|Inserta una representación de texto de un objeto `thread::id` en una secuencia.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


