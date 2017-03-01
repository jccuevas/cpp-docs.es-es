---
title: '&lt;mutex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <mutex>
dev_langs:
- C++
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
caps.latest.revision: 17
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
ms.openlocfilehash: 7e6aaf9ae1817da4a532b00fe0bf54afc5e9cd17
ms.lasthandoff: 02/24/2017

---
# <a name="ltmutexgt"></a>&lt;mutex&gt;
Incluya el encabezado estándar \<mutex> para definir las clases `mutex`, `recursive_mutex`, `timed_mutex` y `recursive_timed_mutex`; las plantillas `lock_guard` y `unique_lock`; y tipos y funciones auxiliares que definen regiones de código de exclusión mutua.  
  
> [!WARNING]
>  Los tipos de sincronización de la biblioteca estándar de C++ en Visual Studio 2015 se basan en los primitivos de sincronización de Windows y ya no usan ConcRT (salvo cuando la plataforma de destino es Windows XP). Los tipos definidos en \<mutex> no deben usarse con ninguna función o tipo ConcRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <mutex>  
```  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En el código que se compila con **/CLR**, este encabezado está bloqueado.  
  
 Las clases `mutex` y `recursive_mutex` son *tipos de exclusión mutua*. Un tipo de exclusión mutua tiene un constructor predeterminado y un destructor que no inicia excepciones. Estos objetos tienen métodos que proporcionan exclusión mutua cuando varios subprocesos intentan bloquear el mismo objeto. En concreto, un tipo de exclusión mutua contiene los métodos `lock`, `try_lock` y `unlock`:  
  
-   El método `lock` bloquea el subproceso que realiza la llamada hasta que el subproceso obtenga la propiedad de la exclusión mutua. Su valor devuelto se omite.  
  
-   El método `try_lock` intenta obtener la propiedad de la exclusión mutua sin bloquear. Su tipo de valor devuelto se puede convertir a `bool` y `true` si el método obtiene la propiedad, pero en caso contrario es `false`.  
  
-   El método `unlock` libera la propiedad de la exclusión mutua del subproceso que llama.  
  
 Puede usar tipos de exclusión mutua como argumentos de tipo para crear instancias de las plantillas `lock_guard` y `unique_lock`. Puede usar objetos de estos tipos como el argumento `Lock` para las funciones miembro de espera en la plantilla [condition_variable_any](../standard-library/condition-variable-any-class.md).  
  
 Un *tipo de exclusión mutua cronometrado* satisface los requisitos de un tipo de exclusión mutua. Además, tiene los métodos `try_lock_for` y `try_lock_until` que deben ser invocables mediante el uso de un argumento y deben devolver un tipo que se pueda convertir en `bool`. Un tipo de exclusión mutua cronometrado puede definir estas funciones mediante argumentos adicionales, siempre que todos esos argumentos adicionales tengan valores predeterminados.  
  
-   Se debe poder llamar al método `try_lock_for` mediante el uso de un argumento, `Rel_time`, cuyo tipo es una creación de instancias de [chrono::duration](../standard-library/duration-class.md). El método intenta obtener la propiedad de la exclusión mutua, pero devuelve dentro del período de tiempo designado por `Rel_time`, independientemente de que la operación se haya realizado o no correctamente. El valor devuelto se convierte en `true` si el método obtiene la propiedad; de lo contrario, se convierte en `false`.  
  
-   Se debe poder llamar al método `try_lock_until` mediante el uso de un argumento, `Abs_time`, cuyo tipo es una creación de instancias de [chrono::time_point](../standard-library/time-point-class.md). El método intenta obtener la propiedad de la exclusión mutua, pero devuelve antes de que se supere el tiempo designado por `Abs_time`, independientemente de que la operación se haya realizado o no correctamente. El valor devuelto se convierte en `true` si el método obtiene la propiedad; de lo contrario, se convierte en `false`.  
  
 Un tipo de exclusión mutua también se conoce como un *tipo bloqueable*. Si no proporciona la función miembro `try_lock`, es un *tipo bloqueable básico*. Un tipo de exclusión mutua cronometrado también se conoce como un *tipo bloqueable cronometrado*.  
  
### <a name="classes"></a>Clases  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[lock_guard (Clase)](../standard-library/lock-guard-class.md)|Representa una plantilla de la que se pueden crear instancias para crear un objeto cuyo destructor desbloquea una `mutex`.|  
|[mutex (Clase, biblioteca estándar de C++)](../standard-library/mutex-class-stl.md)|Representa un tipo de exclusión mutua. Use objetos de este tipo para aplicar la exclusión mutua dentro de un programa.|  
|[recursive_mutex (Clase)](../standard-library/recursive-mutex-class.md)|Representa un tipo de exclusión mutua. Al contrario que la clase `mutex`, el comportamiento de la llamada a métodos de bloqueos para objetos que ya estén bloqueados está bien definido.|  
|[recursive_timed_mutex (Clase)](../standard-library/recursive-timed-mutex-class.md)|Representa un tipo de exclusión mutua cronometrado. Use objetos de este tipo para aplicar una exclusión mutua que tenga un bloqueo limitado por tiempo dentro de un programa. A diferencia de los objetos de tipo `timed_mutex`, el efecto de llamar a métodos de bloqueos de objetos `recursive_timed_mutex` está bien definido.|  
|[timed_mutex (Clase)](../standard-library/timed-mutex-class.md)|Representa un tipo de exclusión mutua cronometrado. Use objetos de este tipo para aplicar una exclusión mutua que tenga un bloqueo limitado por tiempo dentro de un programa.|  
|[unique_lock (Clase)](../standard-library/unique-lock-class.md)|Representa una plantilla de la que se pueden crear instancias para crear objetos que administren el bloqueo y desbloqueo de una `mutex`.|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[call_once (Función)](../standard-library/mutex-functions.md#call_once_function)|Proporciona un mecanismo para llamar exactamente una vez durante la ejecución a un objeto especificado que se puede llamar.|  
|[lock (Función)](../standard-library/mutex-functions.md#lock_function)|Intenta bloquear todos los argumentos sin interbloqueo.|  
  
### <a name="structs"></a>Structs  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[adopt_lock_t (Estructura)](../standard-library/adopt-lock-t-structure.md)|Representa un tipo que se utiliza para definir un `adopt_lock`.|  
|[defer_lock_t (Estructura)](../standard-library/defer-lock-t-structure.md)|Representa un tipo que define un objeto `defer_lock` que se utiliza para seleccionar uno de los constructores sobrecargados de `unique_lock`.|  
|[once_flag (Estructura)](../standard-library/once-flag-structure.md)|Representa un `struct` que se utiliza con la función de plantilla `call_once` para asegurarse de que solo se llame una vez al código de inicialización, incluso ante la presencia de varios subprocesos de ejecución.|  
|[try_to_lock_t (Estructura)](../standard-library/try-to-lock-t-structure.md)|Representa un `struct` que define un objeto `try_to_lock` y que se utiliza para seleccionar uno de los constructores sobrecargados de `unique_lock`.|  
  
### <a name="variables"></a>Variables  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[adopt_lock (Variable)](../standard-library/mutex-functions.md#adopt_lock_variable)|Representa un objeto que se puede pasar a los constructores para `lock_guard` y `unique_lock` para indicar que el objeto de exclusión mutua que también se pasa al constructor está bloqueado.|  
|[defer_lock (Variable)](../standard-library/mutex-functions.md#defer_lock_variable)|Representa un objeto que se puede pasar al constructor de `unique_lock` para indicar que el constructor no debería bloquear el objeto de exclusión mutua que también se pasa a él.|  
|[try_to_lock (Variable)](../standard-library/mutex-functions.md#try_to_lock_variable)|Representa un objeto que se puede pasar al constructor de `unique_lock` para indicar que el constructor debería intentar desbloquear la `mutex` que también se pasa a él sin bloquearla.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)




