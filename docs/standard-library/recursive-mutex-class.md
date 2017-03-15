---
title: recursive_mutex (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::recursive_mutex
dev_langs:
- C++
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c82c8302be5d3e01de90adda2049a022100b8443
ms.lasthandoff: 02/24/2017

---
# <a name="recursivemutex-class"></a>recursive_mutex (Clase)
Representa un *tipo de exclusión mutua*. Al contrario que [mutex](../standard-library/mutex-class-stl.md), el comportamiento de las llamadas a métodos de bloqueo para objetos que ya están bloqueados está bien definido.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class recursive_mutex;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[recursive_mutex (Constructor)](#recursive_mutex__recursive_mutex_constructor)|Construye un objeto `recursive_mutex`.|  
|[~recursive_mutex (Destructor)](#recursive_mutex___dtorrecursive_mutex_destructor)|Libera todos los recursos usados por el objeto `recursive_mutex`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[lock](#recursive_mutex__lock_method)|Bloquea el subproceso de llamada hasta que este obtiene la propiedad de la exclusión mutua.|  
|[try_lock](#recursive_mutex__try_lock_method)|Intenta obtener la propiedad de la exclusión mutua sin bloquearla.|  
|[unlock](#recursive_mutex__unlock_method)|Libera la propiedad de la exclusión mutua.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namerecursivemutexlockmethoda--lock"></a><a name="recursive_mutex__lock_method"></a> lock  
 Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el subproceso que realiza la llamada ya posee `mutex`, el método se devuelve inmediatamente, y el bloqueo anterior permanece vigente.  
  
##  <a name="a-namerecursivemutexrecursivemutexconstructora--recursivemutex"></a><a name="recursive_mutex__recursive_mutex_constructor"></a> recursive_mutex  
 Crea un objeto `recursive_mutex` que no está bloqueado.  
  
```cpp  
recursive_mutex();
```  
  
##  <a name="a-namerecursivemutexdtorrecursivemutexdestructora--recursivemutex"></a><a name="recursive_mutex___dtorrecursive_mutex_destructor"></a> ~recursive_mutex  
 Libera todos los recursos usados por el objeto.  
  
```cpp  
~recursive_mutex();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.  
  
##  <a name="a-namerecursivemutextrylockmethoda--trylock"></a><a name="recursive_mutex__try_lock_method"></a> try_lock  
 Intenta obtener la propiedad de `mutex` sin bloquearlo.  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si el método obtiene correctamente la propiedad de `mutex` o si el subproceso que realiza la llamada ya posee `mutex`; de otro modo, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Si el subproceso que realiza la llamada ya posee `mutex`, la función devuelve `true` inmediatamente, y el bloqueo anterior permanece vigente.  
  
##  <a name="a-namerecursivemutexunlockmethoda--unlock"></a><a name="recursive_mutex__unlock_method"></a> unlock  
 Libera la propiedad de la exclusión mutua.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método libera la propiedad de `mutex` solo después de que se llame tantas veces como se ha llamado a [lock](#recursive_mutex__lock_method) y [try_lock](#recursive_mutex__try_lock_method) correctamente en el objeto `recursive_mutex`.  
  
 Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




