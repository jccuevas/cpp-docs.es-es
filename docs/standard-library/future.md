---
title: '&lt;future&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <future>
dev_langs:
- C++
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86978cd4549f0672dac7cad0e4713380ea189c27
ms.openlocfilehash: e2ebbb8eb6e6f250376b0ef2b43dae261a642d69
ms.contentlocale: es-es
ms.lasthandoff: 04/18/2017

---
# <a name="ltfuturegt"></a>&lt;future&gt;
Incluya el encabezado estándar \<future> para definir clases de plantilla y plantillas auxiliares que simplifican la ejecución de una función, posiblemente en un subproceso diferente, y la recuperación de su resultado. El resultado es el valor devuelto por la función o una excepción que la función emite pero que no se detecta en la función.  
  
 Este encabezado utiliza el runtime de simultaneidad (ConcRT) para que pueda utilizarlo junto con otros mecanismos de ConcRT. Para obtener más información sobre ConcRT, vea [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <future>  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En el código compilado mediante **/CLR**, este encabezado está bloqueado.  
  
 Un *proveedor asincrónico* almacena el resultado de una llamada de función. Se usa un *objeto de devolución asincrónico* para recuperar el resultado de una llamada de función. Un *estado asincrónico asociado* proporciona la comunicación entre un proveedor asincrónico y uno o varios objetos de devolución asincrónicos.  
  
 Un programa no crea directamente ningún objeto con un estado asincrónico asociado. El programa crea un proveedor asincrónico cuando necesita uno y a partir de él crea un objeto de devolución asincrónico que comparte su estado asincrónico asociado con el proveedor. Los proveedores asincrónicos y los objetos de devolución asincrónicos administran los objetos que contienen su estado asincrónico asociado compartido. Cuando el último objeto que hace referencia al estado asincrónico asociado lo libera, se destruye el objeto que contiene el estado asincrónico asociado.  
  
 Un proveedor asincrónico o un objeto de devolución asincrónico que no tiene ningún estado asincrónico asociado está *vacío*.  
  
 Un estado asincrónico asociado está *listo* únicamente si su proveedor asincrónico ha almacenado un valor devuelto o una excepción.  
  
 La función de plantilla `async` y las clases de plantilla `promise` y `packaged_task` son proveedores asincrónicos. Las clases de plantilla `future` y `shared_future` describen objetos de devolución asincrónicos.  
  
 Cada una de las clases de plantilla `promise`, `future` y `shared_future` tiene una especialización para el tipo `void` y una especialización parcial para almacenar y recuperar un valor por referencia. Estas especializaciones solo difieren de la plantilla principal en las signaturas y la semántica de las funciones que almacenan y recuperan el valor devuelto.  
  
 Las clases de plantilla `future` y `shared_future` nunca se bloquean en sus destructores, excepto en un caso que se conserva por compatibilidad con versiones anteriores: a diferencia de todos los demás future, para un `future` (o para el último `shared_future`) que está adjunto a una tarea iniciada con `std::async`, el destructor se bloquea si la tarea no se ha completado; es decir, se bloquea si este subproceso no ha llamado aún a `.get()` o `.wait()` y la tarea todavía se está ejecutando. Se ha agregado la siguiente nota de uso a la descripción de `std::async` en el borrador del estándar: "[Nota: si un future obtenido de std::async se desplaza fuera del ámbito local, otro código que utilice el future debe saber que el destructor del future puede bloquearse para que el estado compartido esté listo.—fin de la nota]" En todos los demás casos, los destructores de `future` y `shared_future` son necesarios y se garantiza que nunca se bloquean.  
  
## <a name="members"></a>Miembros  
  
### <a name="classes"></a>Clases  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[future (Clase)](../standard-library/future-class.md)|Describe un objeto de devolución asincrónico.|  
|[future_error (Clase)](../standard-library/future-error-class.md)|Describe un objeto de excepción que pueden producir los métodos de tipos que administran objetos `future`.|  
|[packaged_task (Clase)](../standard-library/packaged-task-class.md)|Describe un proveedor asincrónico que es un contenedor de llamadas y cuya signatura de llamada es `Ty(ArgTypes...)`. Su estado asincrónico asociado contiene una copia del objeto al que se puede llamar, además del resultado posible.|  
|[promise (Clase)](../standard-library/promise-class.md)|Describe un proveedor asincrónico.|  
|[shared_future (Clase)](../standard-library/shared-future-class.md)|Describe un objeto de devolución asincrónico. Al contrario que un objeto `future`, un proveedor asincrónico se puede asociar a cualquier número de objetos `shared_future`.|  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[is_error_code_enum (Estructura)](../standard-library/is-error-code-enum-structure.md)|Especialización que indica que se puede utilizar `future_errc` para almacenar un elemento `error_code`.|  
|[uses_allocator (Estructura)](../standard-library/uses-allocator-structure.md)|Especialización que siempre contiene true.|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[async](../standard-library/future-functions.md#async)|Representa un proveedor asincrónico.|  
|[future_category](../standard-library/future-functions.md#future_category)|Devuelve una referencia al objeto `error_category` que caracteriza los errores asociados a objetos `future`.|  
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Crea un elemento `error_code` que tiene el objeto `error_category` que caracteriza los errores de `future`.|  
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Crea un elemento `error_condition` que tiene el objeto `error_category` que caracteriza los errores de `future`.|  
|[swap](../standard-library/future-functions.md#swap)|Intercambia el estado asincrónico asociado de un objeto `promise` con el de otro.|  
  
### <a name="enumerations"></a>Enumeraciones  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[future_errc](../standard-library/future-enums.md#future_errc)|Proporciona nombres simbólicos para los errores notificados por la clase `future_error`.|  
|[future_status](../standard-library/future-enums.md#future_status)|Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.|  
|[iniciar](../standard-library/future-enums.md#launch)|Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla `async`.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)




