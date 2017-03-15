---
title: "mutex (Clase, biblioteca estándar de C++)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::mutex
dev_langs:
- C++
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
caps.latest.revision: 11
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
ms.openlocfilehash: ff3e7e71c678ffc9bdead79ec56ad94f8e297a16
ms.lasthandoff: 02/24/2017

---
# <a name="mutex-class-c-standard-library"></a>mutex (Clase, biblioteca estándar de C++)
Representa un *tipo de exclusión mutua*. Los objetos de este tipo se pueden usar para aplicar la exclusión mutua dentro de un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class mutex;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[mutex::mutex Constructor](#mutex__mutex_constructor)|Construye un objeto `mutex`.|  
|[mutex::~mutex Destructor](#mutex___dtormutex_destructor)|Libera todos los recursos utilizados por el objeto `mutex`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[mutex::lock (Método)](#mutex__lock_method)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|  
|[mutex::native_handle (Método)](#mutex__native_handle_method)|Devuelve el tipo específico de la implementación que representa el identificador de exclusión mutua.|  
|[mutex::try_lock (Método)](#mutex__try_lock_method)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|  
|[mutex::unlock (Método)](#mutex__unlock_method)|Libera la propiedad de `mutex`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namemutexlockmethoda--mutexlock-method"></a><a name="mutex__lock_method"></a> mutex::lock (Método)  
 Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.  
  
##  <a name="a-namemutexmutexconstructora--mutexmutex-constructor"></a><a name="mutex__mutex_constructor"></a> mutex::mutex (Constructor)  
 Crea un objeto `mutex` que no está bloqueado.  
  
```cpp  
constexpr mutex() noexcept;
```  
  
##  <a name="a-namemutexdtormutexdestructora--mutexmutex-destructor"></a><a name="mutex___dtormutex_destructor"></a> mutex::~mutex (Destructor)  
 Libera todos los recursos usados por el objeto `mutex`.  
  
```cpp  
~mutex();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.  
  
##  <a name="a-namemutexnativehandlemethoda--mutexnativehandle-method"></a><a name="mutex__native_handle_method"></a> mutex::native_handle (Método)  
 Devuelve el tipo específico de la implementación que representa el identificador de exclusión mutua. El controlador de exclusión mutua puede usarse en aspectos específicos de la implementación.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `native_handle_type` se define como un `Concurrency::critical_section *` que se convierte en `void *`.  
  
##  <a name="a-namemutextrylockmethoda--mutextrylock-method"></a><a name="mutex__try_lock_method"></a> mutex::try_lock (Método)  
 Intenta obtener la propiedad de `mutex` sin bloquearlo.  
  
```cpp  
bool try_lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es `true` si el método obtiene correctamente la propiedad de `mutex`; de lo contrario, es `false`.  
  
### <a name="remarks"></a>Comentarios  
 Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.  
  
##  <a name="a-namemutexunlockmethoda--mutexunlock-method"></a><a name="mutex__unlock_method"></a> mutex::unlock (Método)  
 Libera la propiedad de `mutex`.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




