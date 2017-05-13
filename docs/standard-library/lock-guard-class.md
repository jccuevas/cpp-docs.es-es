---
title: Clase lock_guard | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: 9
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 047c7ab9db009bceafe47bb0ae53b876adad81b5
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="lockguard-class"></a>lock_guard (Clase)
Representa una plantilla de la que se pueden crear instancias para crear un objeto cuyo destructor desbloquea una `mutex`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Mutex>
class lock_guard;
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento de plantilla `Mutex` debe nombrar un *tipo de exclusión mutua*.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`lock_guard::mutex_type`|Sinónimo del argumento de plantilla `Mutex`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[lock_guard](#lock_guard)|Construye un objeto `lock_guard`.|  
|[Destructor lock_guard::~lock_guard](#dtorlock_guard_destructor)|Desbloquea el objeto `mutex` que se pasó al constructor.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<mutex >  
  
 **Espacio de nombres:** std  
  
##  <a name="lock_guard"></a>  Constructor lock_guard::lock_guard  
 Construye un objeto `lock_guard`.  
  
```cpp  
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```  
  
### <a name="parameters"></a>Parámetros  
 `Mtx`  
 Objeto de *tipo de exclusión mutua*.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor crea un objeto de tipo `lock_guard` y bloquea `Mtx`. Si `Mtx` no es una exclusión mutua recursiva, debe estar desbloqueado cuando se llama a este constructor.  
  
 El segundo constructor no bloquea `Mtx`. `Mtx` debe estar bloqueado cuando se llama a este constructor. El constructor no inicia excepciones.  
  
##  <a name="dtorlock_guard_destructor"></a>  Destructor lock_guard::~lock_guard  
 Desbloquea el objeto `mutex` que se pasó al constructor.  
  
```
~lock_guard() noexcept;
```  
  
### <a name="remarks"></a>Comentarios  
 Si `mutex` no existe cuando se ejecuta el destructor, el comportamiento es indefinido.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




