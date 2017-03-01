---
title: Funciones y variables &lt;mutex&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: a3bb29348b6bf7da235e608a915bcd10391dcac6
ms.lasthandoff: 02/24/2017

---
# <a name="ltmutexgt-functions-and-variables"></a>Funciones y variables &lt;mutex&gt;
||||  
|-|-|-|  
|[adopt_lock (Variable)](#adopt_lock_variable)|[call_once (Función)](#call_once_function)|[defer_lock (Variable)](#defer_lock_variable)|  
|[lock (Función)](#lock_function)|[try_to_lock (Variable)](#try_to_lock_variable)|  
  
##  <a name="a-nameadoptlockvariablea--adoptlock-variable"></a><a name="adopt_lock_variable"></a> adopt_lock (Variable)  
 Representa un objeto que se puede pasar a los constructores de [lock_guard](../standard-library/lock-guard-class.md) y [unique_lock](../standard-library/unique-lock-class.md) para indicar que el objeto de exclusión mutua que también se pasa al constructor está bloqueado.  
  
```cpp  
const adopt_lock_t adopt_lock;
```  
  
##  <a name="a-namecalloncefunctiona--callonce"></a><a name="call_once_function"></a> call_once  
 Proporciona un mecanismo para llamar exactamente una vez durante la ejecución a un objeto especificado que se puede llamar.  
  
```
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```  
  
### <a name="parameters"></a>Parámetros  
 `Flag`  
 Un objeto [once_flag](../standard-library/once-flag-structure.md) que garantiza que solo se llama una vez al objeto que se puede llamar.  
  
 `F`  
 Un objeto al que se puede llamar.  
  
 `A`  
 Lista de argumentos.  
  
### <a name="remarks"></a>Comentarios  
 Si `Flag` no es válido, la función produce un [system_error](../standard-library/system-error-class.md) que tiene un código de error de `invalid_argument`. De otro modo, la función de plantilla usa su argumento `Flag` para garantizar que llama correctamente a `F(A...)` exactamente una vez, independientemente de cuántas veces se llame a la función de plantilla. Si `F(A...)` se cierra emitiendo una excepción, la llamada no se ha realizado correctamente.  
  
##  <a name="a-namedeferlockvariablea--deferlock-variable"></a><a name="defer_lock_variable"></a> defer_lock (Variable)  
 Representa un objeto que puede pasarse al constructor para [unique_lock](../standard-library/unique-lock-class.md). Esto indica que el constructor no debe bloquear el objeto mutex que también se le está pasando.  
  
```cpp  
const defer_lock_t defer_lock;
```  
  
##  <a name="a-namelockfunctiona--lock"></a><a name="lock_function"></a> lock  
 Intenta bloquear todos los argumentos sin interbloqueo.  
  
```cpp  
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```  
  
### <a name="remarks"></a>Comentarios  
 Los argumentos de la función de plantilla debe ser *tipos mutex*, excepto que las llamadas a `try_lock` pueden producir excepciones.  
  
 La función bloquea todos sus argumentos sin interbloqueo mediante llamadas a `lock`, `try_lock` y `unlock`. Si una llamada a `lock` o `try_lock` produce una excepción, la función llama a `unlock` en cualquiera de los objetos mutex que se han bloqueado correctamente antes de volver a producir la excepción.  
  
##  <a name="a-nametrytolockvariablea--trytolock-variable"></a><a name="try_to_lock_variable"></a> try_to_lock (Variable)  
 Representa un objeto que se puede pasar al constructor de [unique_lock](../standard-library/unique-lock-class.md) para indicar que el constructor debería intentar desbloquear la `mutex` que también se pasa a este sin bloquearla.  
  
```cpp  
const try_to_lock_t try_to_lock;
```  
  
## <a name="see-also"></a>Vea también  
 [\<mutex>](../standard-library/mutex.md)




