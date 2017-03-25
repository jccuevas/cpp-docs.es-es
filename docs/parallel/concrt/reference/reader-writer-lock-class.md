---
title: reader_writer_lock (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
dev_langs:
- C++
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: b5107923baa7d22e6a98c6617a22a883c4d84125
ms.lasthandoff: 03/17/2017

---
# <a name="readerwriterlock-class"></a>reader_writer_lock (Clase)
Un bloqueo de lectura o escritura basado en cola, con preferencia del sistema de escritura y con giro solo local. El bloqueo permite el acceso primero en entrar, primero en salir (FIFO) a los sistemas de escritura y lectores agotados bajo una carga continua de sistemas de escritura.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class reader_writer_lock;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-classes"></a>Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[reader_writer_lock:: scoped_lock (clase)](#scoped_lock_class)|Una excepción segura del contenedor RAII que se puede utilizar para adquirir `reader_writer_lock` bloquear objetos como un sistema de escritura.|  
|[reader_writer_lock:: scoped_lock_read (clase)](#scoped_lock_read_class)|Una excepción segura del contenedor RAII que se puede utilizar para adquirir `reader_writer_lock` objetos de bloqueo como lector.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|Construye un nuevo objeto `reader_writer_lock`.|  
|[~ reader_writer_lock (destructor)](#dtor)|Destruye el objeto `reader_writer_lock`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[lock](#lock)|Adquiere el bloqueo de lector y escritor como escritor.|  
|[lock_read](#lock_read)|Adquiere el bloqueo de lector y escritor como lector. Si hay sistemas de escritura, los lectores activos tienen que esperar hasta que hayan terminado. El lector simplemente registra un interés en el bloqueo y espera para que escritores de liberarlo.|  
|[try_lock](#try_lock)|Intenta adquirir el bloqueo de lector y escritor como un sistema de escritura sin bloqueo.|  
|[try_lock_read](#try_lock_read)|Intenta adquirir el bloqueo de lector y escritor como un lector sin bloqueo.|  
|[unlock](#unlock)|Desbloquea el bloqueo de lector y escritor según quién bloqueó, lector o escritor.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [estructuras de datos de sincronización](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `reader_writer_lock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="lock"></a>bloqueo 

 Adquiere el bloqueo de lector y escritor como escritor.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Comentarios  
 A menudo es más seguro usar la [scoped_lock](#scoped_lock_class) construcción para adquirir y liberar un `reader_writer_lock` objeto como un sistema de escritura en una excepción forma segura.  
  
 Después de un sistema de escritura intenta adquirir el bloqueo, cualquier lector futuro se bloqueará hasta que los escritores ha adquirido y liberado el bloqueo. Este bloqueo está orientado hacia los escritores y puede privar a los lectores bajo una carga continua de sistemas de escritura.  
  
 Escritores se encadenan para que un escritor de salir del bloqueo libera el escritor en la línea siguiente.  
  
 Si el bloqueo ya es retenido por el contexto de llamada, un [improper_lock](improper-lock-class.md) se producirá la excepción.  
  
##  <a name="lock_read"></a>lock_read 

 Adquiere el bloqueo de lector y escritor como lector. Si hay sistemas de escritura, los lectores activos tienen que esperar hasta que hayan terminado. El lector simplemente registra un interés en el bloqueo y espera para que escritores de liberarlo.  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>Comentarios  
 A menudo es más seguro usar la [scoped_lock_read](#scoped_lock_read_class) construcción para adquirir y liberar un `reader_writer_lock` objeto como lector en una excepción forma segura.  
  
 Si hay escritores que esperan el bloqueo, el lector esperará hasta que hayan adquirido y liberado el bloqueo todos los escritores en línea. Este bloqueo está orientado hacia los escritores y puede privar a los lectores bajo una carga continua de sistemas de escritura.  
  
##  <a name="ctor"></a>reader_writer_lock 

 Construye un nuevo objeto `reader_writer_lock`.  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a>~ reader_writer_lock 

 Destruye el objeto `reader_writer_lock`.  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>Comentarios  
 Se espera que ya no se mantiene el bloqueo cuando el destructor se ejecuta. Lo que permite el bloqueo de escritor de lector destruya con el bloqueo, sigue dando resultados de comportamiento no definido.  
  
##  <a name="scoped_lock_class"></a>reader_writer_lock:: scoped_lock (clase)  
 Una excepción segura del contenedor RAII que se puede utilizar para adquirir `reader_writer_lock` bloquear objetos como un sistema de escritura.  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock 

Construye un `scoped_lock` de objetos y adquiere el `reader_writer_lock` objeto pasado en el `_Reader_writer_lock` parámetro como un sistema de escritura. Si otro subproceso mantiene el bloqueo, esta llamada se bloqueará.  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Reader_writer_lock`  
 La `reader_writer_lock` objeto a adquirir como un sistema de escritura.  
  
## <a name="scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock 

Destruye un `reader_writer_lock` de objetos y libera el bloqueo proporcionado en su constructor.   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class"></a>reader_writer_lock:: scoped_lock_read (clase)  
 Una excepción segura del contenedor RAII que se puede utilizar para adquirir `reader_writer_lock` objetos de bloqueo como lector.  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a>try_lock 

 Intenta adquirir el bloqueo de lector y escritor como un sistema de escritura sin bloqueo.  

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read 

Construye un `scoped_lock_read` de objetos y adquiere el `reader_writer_lock` objeto pasado en el `_Reader_writer_lock` parámetro como lector. Si el bloqueo se mantiene por otro subproceso como un sistema de escritura o hay sistemas de escritura pendientes, esta llamada se bloqueará.  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Reader_writer_lock`  
 La `reader_writer_lock` objeto que se va a adquirir como lector.  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read (destructor)
Destruye un `scoped_lock_read` de objetos y libera el bloqueo proporcionado en su constructor.  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a>try_lock 

```
bool try_lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se adquirió el bloqueo, el valor `true`; en caso contrario, el valor `false`.  
  
##  <a name="try_lock_read"></a>try_lock_read 

 Intenta adquirir el bloqueo de lector y escritor como un lector sin bloqueo.  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se adquirió el bloqueo, el valor `true`; en caso contrario, el valor `false`.  
  
##  <a name="unlock"></a>desbloquear 

 Desbloquea el bloqueo de lector y escritor según quién bloqueó, lector o escritor.  
  
```
void unlock();
```  
  
### <a name="remarks"></a>Comentarios  
 Si hay escritores que esperan el bloqueo, la liberación del bloqueo siempre irá al sistema de escritura siguiente en orden FIFO. Este bloqueo está orientado hacia los escritores y puede privar a los lectores bajo una carga continua de sistemas de escritura.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [critical_section (clase)](critical-section-class.md)

