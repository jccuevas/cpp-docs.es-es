---
title: "&lt;mutex&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<mutex>"
dev_langs: 
  - "C++"
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;mutex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado estándar \<mutex\> para definir las clases`mutex`, `recursive_mutex`, `timed_mutex` y `recursive_timed_mutex`; las plantillas `lock_guard` y `unique_lock`; y tipos y funciones auxiliares que definen regiones de código de exclusión mutua.  
  
> [!WARNING]
>  Los tipos de sincronización de STL en Visual Studio 2015 se basan en los primitivos de sincronización de Windows y ya no utilizan ConcRT \(salvo cuando la plataforma de destino es Windows XP\).  Los tipos definidos en \<mutex\> no deben utilizarse con ninguna función o tipo ConcRT.  
  
## Sintaxis  
  
```cpp  
#include <mutex>  
```  
  
## Comentarios  
  
> [!NOTE]
>  En el código compilado mediante **\/clr** o **\/clr:pure**, este encabezado está bloqueado.  
  
 Las clases `mutex` y `recursive_mutex` son *tipos de exclusión mutua*.  Un tipo de exclusión mutua tiene un constructor predeterminado y un destructor que no inicia excepciones.  Estos objetos tienen métodos que proporcionan exclusión mutua cuando varios subprocesos intentan bloquear el mismo objeto.  En concreto, un tipo de exclusión mutua contiene los métodos `lock`, `try_lock` y `unlock`:  
  
-   El método `lock` bloquea el subproceso que realiza la llamada hasta que el subproceso obtenga la propiedad de la exclusión mutua.  Su valor devuelto se omite.  
  
-   El método `try_lock` intenta obtener la propiedad de la exclusión mutua sin bloquear.  Su tipo de valor devuelto se puede convertir a `bool` y `true` si el método obtiene la propiedad, pero en caso contrario es `false`.  
  
-   El método `unlock` libera la propiedad de la exclusión mutua del subproceso que llama.  
  
 Puede usar tipos de exclusión mutua como argumentos de tipo para crear instancias de las plantillas `lock_guard` y `unique_lock`.  Puede usar objetos de estos tipos como el  argumento `Lock` para las funciones miembro de espera en la plantilla [condition\_variable\_any](../standard-library/condition-variable-any-class.md).  
  
 Un *tipo de exclusión mutua cronometrado* satisface los requisitos de un tipo de exclusión mutua.  Además, tiene los métodos `try_lock_for` y `try_lock_until` que deben ser invocables mediante el uso de un argumento y deben devolver un tipo que se pueda convertir en `bool`.  Un tipo de exclusión mutua cronometrado puede definir estas funciones mediante argumentos adicionales, siempre que todos esos argumentos adicionales tengan valores predeterminados.  
  
-   Se debe poder llamar al método `try_lock_for` mediante el uso de un argumento, `Rel_time`, cuyo tipo es una instancia de [chrono::duration](../standard-library/duration-class.md).  El método intenta obtener la propiedad de la exclusión mutua, pero devuelve dentro del período de tiempo designado por `Rel_time`, independientemente de que la operación se haya realizado o no correctamente.  El valor devuelto se convierte en `true` si el método obtiene la propiedad; de lo contrario, se convierte en `false`.  
  
-   Se debe poder llamar al método `try_lock_until` mediante el uso de un argumento, `Abs_time`, cuyo tipo es una instancia de [chrono::time\_point](../standard-library/time-point-class.md).  El método intenta obtener la propiedad de la exclusión mutua, pero devuelve antes de que se supere el tiempo designado por `Abs_time`, independientemente de que la operación se haya realizado o no correctamente.  El valor devuelto se convierte en `true` si el método obtiene la propiedad; de lo contrario, se convierte en `false`.  
  
 Un tipo de exclusión mutua también se conoce como un *tipo bloqueable*.  Si no proporciona la función miembro `try_lock`, es un *tipo bloqueable básico*.  Un tipo de exclusión mutua cronometrado también se conoce como un *tipo bloqueable cronometrado*.  
  
### Clases  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[lock\_guard \(Clase\)](../standard-library/lock-guard-class.md)|Representa una plantilla de la que se pueden crear instancias para crear un objeto cuyo destructor desbloquea una `mutex`.|  
|[mutex \(Clase, STL\)](../standard-library/mutex-class-stl.md)|Representa un tipo de exclusión mutua.  Use objetos de este tipo para aplicar la exclusión mutua dentro de un programa.|  
|[recursive\_mutex \(Clase\)](../standard-library/recursive-mutex-class.md)|Representa un tipo de exclusión mutua.  Al contrario que la clase `mutex`, el comportamiento de la llamada a métodos de bloqueos para objetos que ya estén bloqueados está bien definido.|  
|[recursive\_timed\_mutex \(Clase\)](../standard-library/recursive-timed-mutex-class.md)|Representa un tipo de exclusión mutua cronometrado.  Use objetos de este tipo para aplicar una exclusión mutua que tenga un bloqueo limitado por tiempo dentro de un programa.  A diferencia de los objetos de tipo `timed_mutex`, el efecto de llamar a métodos de bloqueos de objetos `recursive_timed_mutex` está bien definido.|  
|[timed\_mutex \(Clase\)](../standard-library/timed-mutex-class.md)|Representa un tipo de exclusión mutua cronometrado.  Use objetos de este tipo para aplicar una exclusión mutua que tenga un bloqueo limitado por tiempo dentro de un programa.|  
|[unique\_lock \(Clase\)](../standard-library/unique-lock-class.md)|Representa una plantilla de la que se pueden crear instancias para crear objetos que administren el bloqueo y desbloqueo de una `mutex`.|  
  
### Funciones  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[call\_once \(Función\)](../Topic/call_once%20Function.md)|Proporciona un mecanismo para llamar exactamente una vez durante la ejecución a un objeto especificado que se puede llamar.|  
|[lock \(Función\)](../Topic/lock%20Function.md)|Intenta bloquear todos los argumentos sin interbloqueo.|  
  
### Structs  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[adopt\_lock\_t \(Estructura\)](../standard-library/adopt-lock-t-structure.md)|Representa un tipo que se utiliza para definir un `adopt_lock`.|  
|[defer\_lock\_t \(Estructura\)](../standard-library/defer-lock-t-structure.md)|Representa un tipo que define un objeto `defer_lock` que se utiliza para seleccionar uno de los constructores sobrecargados de `unique_lock`.|  
|[once\_flag \(Estructura\)](../standard-library/once-flag-structure.md)|Representa un `struct` que se utiliza con la función de plantilla `call_once` para asegurarse de que solo se llame una vez al código de inicialización, incluso ante la presencia de varios subprocesos de ejecución.|  
|[try\_to\_lock\_t \(Estructura\)](../standard-library/try-to-lock-t-structure.md)|Representa un `struct` que define un objeto `try_to_lock` y que se utiliza para seleccionar uno de los constructores sobrecargados de `unique_lock`.|  
  
### Variables  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[adopt\_lock \(Variable\)](../Topic/adopt_lock%20Variable.md)|Representa un objeto que se puede pasar a los constructores para `lock_guard` y `unique_lock` para indicar que el objeto de exclusión mutua que también se pasa al constructor está bloqueado.|  
|[defer\_lock \(Variable\)](../Topic/defer_lock%20Variable.md)|Representa un objeto que se puede pasar al constructor de `unique_lock` para indicar que el constructor no debería bloquear el objeto de exclusión mutua que también se pasa a él.|  
|[try\_to\_lock \(Variable\)](../Topic/try_to_lock%20Variable.md)|Representa un objeto que se puede pasar al constructor de `unique_lock` para indicar que el constructor debería intentar desbloquear la `mutex` que también se pasa a él sin bloquearla.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)