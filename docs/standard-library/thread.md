---
title: '&lt;subproceso&gt; | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <thread>
dev_langs: C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0847d92d890026ce6cfb963b022a3859370877fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltthreadgt"></a>&lt;thread&gt;
Incluya el encabezado estándar \<subproceso > para definir la clase `thread` y diversas funciones auxiliares.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En el código compilado mediante **/CLR**, este encabezado está bloqueado.  
  
 El `__STDCPP_THREADS__` macro se define como un valor distinto de cero para indicar que los subprocesos son compatibles con este encabezado.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-classes"></a>Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[thread (Clase)](../standard-library/thread-class.md)|Define un objeto que se utiliza para observar y administrar un subproceso de ejecución en una aplicación.|  
  
### <a name="public-structures"></a>Estructuras públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[hash (Estructura, biblioteca estándar de C++)](../standard-library/hash-structure-stl.md)|Define una función miembro que devuelve un valor que se determina de forma única mediante un `thread::id`. Define la función miembro un [hash](../standard-library/hash-class.md) función que es adecuado para los valores de asignación de tipo `thread::id` a una distribución de valores de índice.|  
  
### <a name="public-functions"></a>Funciones públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[get_id](../standard-library/thread-functions.md#get_id)|Identifica de forma única el subproceso de ejecución actual.|  
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Bloquea el subproceso de llamada.|  
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Bloquea el subproceso de llamada al menos hasta la hora especificada.|  
|[swap](../standard-library/thread-functions.md#swap)|Intercambia los Estados de dos `thread` objetos.|  
|[yield](../standard-library/thread-functions.md#yield)|Indica al sistema operativo que ejecute otros subprocesos, incluso si el subproceso actual seguiría ejecutándose en condiciones normales.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operador > = (operador)](../standard-library/thread-operators.md#op_gt_eq)|Determina si un objeto `thread::id` es mayor o igual que otro objeto.|  
|[operador > (operador)](../standard-library/thread-operators.md#op_gt)|Determina si un objeto `thread::id` es mayor que otro objeto.|  
|[operador < = (operador)](../standard-library/thread-operators.md#op_lt_eq)|Determina si un objeto `thread::id` es menor o igual que otro objeto.|  
|[operador < (operador)](../standard-library/thread-operators.md#op_lt)|Determina si un objeto `thread::id` es menor que otro objeto.|  
|[operador! = (operador)](../standard-library/thread-operators.md#op_neq)|Compara dos objetos `thread::id` para determinar si no son iguales.|  
|[Operator == (operador)](../standard-library/thread-operators.md#op_eq_eq)|Compara dos objetos `thread::id` para determinar si son iguales.|  
|[operador << (operador)](../standard-library/thread-operators.md#op_lt_lt)|Inserta una representación de texto de un objeto `thread::id` en una secuencia.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

