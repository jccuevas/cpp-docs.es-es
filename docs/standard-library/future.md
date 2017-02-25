---
title: "&lt;future&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<future>"
dev_langs: 
  - "C++"
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# &lt;future&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado estándar \<future\> para definir clases de plantilla y plantillas auxiliares que simplifican la ejecución de una función, posiblemente en un subproceso diferente, y la recuperación de su resultado.  El resultado es el valor devuelto por la función o una excepción que la función emite pero que no se detecta en la función.  
  
 Este encabezado utiliza el runtime de simultaneidad \(ConcRT\) para que pueda utilizarlo junto con otros mecanismos de ConcRT.  Para obtener más información sobre ConcRT, vea [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).  
  
## Sintaxis  
  
```cpp  
#include <future>  
```  
  
## Comentarios  
  
> [!NOTE]
>  En el código compilado mediante **\/clr** o **\/clr:pure**, este encabezado está bloqueado.  
  
 Un *proveedor asincrónico* almacena el resultado de una llamada de función.  Se utiliza un *objeto de devolución asincrónico* para recuperar el resultado de una llamada de función.  Un *estado asincrónico asociado* proporciona la comunicación entre un proveedor asincrónico y uno o más objetos de devolución asincrónicos.  
  
 Un programa no crea directamente ningún objeto con un estado asincrónico asociado.  El programa crea un proveedor asincrónico cuando necesita uno y a partir de él crea un objeto de devolución asincrónico que comparte su estado asincrónico asociado con el proveedor.  Los proveedores asincrónicos y los objetos de devolución asincrónicos administran los objetos que contienen su estado asincrónico asociado compartido.  Cuando el último objeto que hace referencia al estado asincrónico asociado lo libera, se destruye el objeto que contiene el estado asincrónico asociado.  
  
 Un proveedor asincrónico o un objeto de devolución asincrónico que no tiene ningún estado asincrónico asociado está *vacío*.  
  
 Un estado asincrónico asociado está *listo* únicamente si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.  
  
 La función de plantilla `async` y las clases de plantilla `promise` y `packaged_task` son proveedores asincrónicos.  Las clases de plantilla `future` y `shared_future` describen objetos de devolución asincrónicos.  
  
 Cada una de las clases de plantilla `promise`, `future` y `shared_future` tiene una especialización para el tipo `void` y una especialización parcial para almacenar y recuperar un valor por referencia.  Estas especializaciones solo difieren de la plantilla principal en las signaturas y la semántica de las funciones que almacenan y recuperan el valor devuelto.  
  
 Las clases de plantilla `future` y `shared_future` nunca se bloquean en sus destructores, excepto en un caso que se conserva por compatibilidad con versiones anteriores: a diferencia de todos los demás future, para un `future` \(o para el último `shared_future`\) que está adjunto a una tarea iniciada con `std::async`, el destructor se bloquea si la tarea no se ha completado; es decir, se bloquea si este subproceso no ha llamado aún a `.get()` o `.wait()` y la tarea todavía se está ejecutando.  Se ha agregado la siguiente nota de uso a la descripción de `std::async` en el borrador del estándar: "\[Nota: si un future obtenido de std::async se desplaza fuera del ámbito local, otro código que utilice el future debe saber que el destructor del future puede bloquearse para que el estado compartido esté listo.—fin de la nota\]" En todos los demás casos, los destructores de `future` y `shared_future` son necesarios y se garantiza que nunca se bloquean.  
  
## Miembros  
  
### Clases  
  
|Name|Descripción|  
|----------|-----------------|  
|[future \(Clase\)](../standard-library/future-class.md)|Describe un objeto de devolución asincrónico.|  
|[future\_error \(Clase\)](../standard-library/future-error-class.md)|Describe un objeto de excepción que pueden producir los métodos de tipos que administran objetos `future`.|  
|[packaged\_task \(Clase\)](../standard-library/packaged-task-class.md)|Describe un proveedor asincrónico que es un contenedor de llamadas y cuya signatura de llamada es `Ty(ArgTypes...)`.  Su estado asincrónico asociado contiene una copia del objeto al que se puede llamar, además del resultado posible.|  
|[promise \(Clase\)](../standard-library/promise-class.md)|Describe un proveedor asincrónico.|  
|[shared\_future \(Clase\)](../standard-library/shared-future-class.md)|Describe un objeto de devolución asincrónico.  Al contrario que un objeto `future`, un proveedor asincrónico se puede asociar a cualquier número de objetos `shared_future`.|  
  
### Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[is\_error\_code\_enum \(Estructura\)](../standard-library/is-error-code-enum-structure.md)|Especialización que indica que se puede utilizar `future_errc` para almacenar un elemento `error_code`.|  
|[uses\_allocator \(Estructura\)](../standard-library/uses-allocator-structure.md)|Especialización que siempre contiene true.|  
  
### Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[async \(Función\)](../Topic/async%20Function.md)|Representa un proveedor asincrónico.|  
|[future\_category \(Función\)](../Topic/future_category%20Function.md)|Devuelve una referencia al objeto `error_category` que caracteriza los errores asociados a objetos `future`.|  
|[make\_error\_code \(Función\)](../Topic/make_error_code%20Function.md)|Crea un elemento `error_code` que tiene el objeto `error_category` que caracteriza los errores de `future`.|  
|[make\_error\_condition \(Función\)](../Topic/make_error_condition%20Function.md)|Crea un elemento `error_condition` que tiene el objeto `error_category` que caracteriza los errores de `future`.|  
|[swap \(función\) \(\<future\>\)](../Topic/swap%20Function%20\(%3Cfuture%3E\).md)|Intercambia el estado asincrónico asociado de un objeto `promise` con el de otro.|  
  
### Enumeraciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[future\_errc \(Enumeración\)](../Topic/future_errc%20Enumeration.md)|Proporciona nombres simbólicos para los errores notificados por la clase `future_error`.|  
|[future\_status \(Enumeración\)](../Topic/future_status%20Enumeration.md)|Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.|  
|[launch \(Enumeración\)](../Topic/launch%20Enumeration.md)|Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla `async`.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)