---
title: "&lt;condition_variable&gt; | Microsoft Docs"
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
  - "<condition_variable>"
dev_langs: 
  - "C++"
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;condition_variable&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las clases [condition\_variable](../standard-library/condition-variable-class.md) y [condition\_variable\_any](../standard-library/condition-variable-any-class.md) que se usan para crear objetos que esperan una condición para llegar a ser true.  
  
 Este encabezado utiliza el runtime de simultaneidad \(ConcRT\) para que pueda utilizarlo junto con otros mecanismos de ConcRT.  Para obtener más información sobre ConcRT, vea [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).  
  
## Sintaxis  
  
```cpp  
#include <condition_variable>  
```  
  
> [!NOTE]
>  En el código compilado mediante **\/clr** o **\/clr:pure**, este encabezado está bloqueado.  
  
### Comentarios  
 El código que espera una variable de la condición debe utilizar `mutex`.  Un subproceso de la llamada debe bloquear `mutex` antes de llamar a las funciones que esperan la variable de la condición.  `mutex` se bloquea cuando la función llamada vuelve.  `mutex` no se bloquea mientras el subproceso espera la condición para convertirse en true.  De modo que no haya resultados imprevisibles, cada subproceso que espera una variable de la condición debe utilizar el mismo objeto de `mutex` .  
  
 Los objetos de `condition_variable_any` tipo se pueden utilizar con una exclusión mutua de cualquier tipo.  El tipo de se utiliza la exclusión mutua que no tiene que proporcionar el método de `try_lock` .  Los objetos de `condition_variable` tipo sólo se pueden utilizar con una exclusión mutua de `unique_lock<mutex>`escrito.  Los objetos de este tipo pueden ser más rápidos que objetos de `condition_variable_any<unique_lock<mutex>>`escrito.  
  
 Para esperar un evento, primero bloquee mutex, y después llame a uno de los métodos de `wait` en la variable de la condición.  La llamada se bloquea de `wait` hasta otros subprocesos señala la variable de la condición.  
  
 *Las atenciones falsas* aparecen cuando los subprocesos que están esperando a variables condition se desbloquean sin notificaciones adecuadas.  Para reconocer tales atenciones falsas, el código que espera una condición para llegar a ser true debe comprobar explícitamente esa condición cuando el código vuelve de una función de espera.  Esto se hace normalmente mediante un bucle; puede utilizar `wait(unique_lock<mutex>& lock, Predicate pred)` para realizar este bucle para usted.  
  
```cpp  
while (condition is false)  
    wait for condition variable;  
```  
  
 Las clases cada uno de `condition_variable_any` y de `condition_variable` tienen tres métodos que esperan una condición.  
  
-   `wait` espera un período de tiempo ilimitado.  
  
-   `wait_until` espera hasta `time`especificado.  
  
-   `wait_for` espera `time interval`especificado.  
  
 Cada uno de estos métodos tiene dos versiones sobrecargadas.  Uno solo espera y puede despertar false.  El otro toma un argumento adicional de la plantilla que define un predicado.  El método no vuelve hasta que el predicado sea `true`.  
  
 Cada clase también tiene dos métodos que se utilizan para notificar a una variable de la condición que la condición es `true`.  
  
-   `notify_one` se reactivará uno de los subprocesos que está esperando la variable de la condición.  
  
-   `notify_all` se reactivará todos los subprocesos que están esperando la variable de la condición.  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [condition\_variable \(Clase\)](../standard-library/condition-variable-class.md)   
 [condition\_variable\_any \(Clase\)](../standard-library/condition-variable-any-class.md)   
 [cv\_status Enumeration](../Topic/cv_status%20Enumeration.md)