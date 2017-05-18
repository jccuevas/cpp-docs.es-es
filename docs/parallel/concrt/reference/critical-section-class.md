---
title: critical_section (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
dev_langs:
- C++
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 58821589a4b7596b80179a77dfd6a5772531f053
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="criticalsection-class"></a>critical_section (Clase)
Una exclusión mutua no reentrante que es explícitamente consciente del runtime de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class critical_section;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`native_handle_type`|Referencia a un objeto `critical_section`.|  
  
### <a name="public-classes"></a>Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[critical_section:: scoped_lock (clase)](#critical_section__scoped_lock_class)|Una excepción segura del contenedor RAII para un `critical_section` objeto.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[critical_section](#ctor)|Construye una nueva sección crítica.|  
|[~ critical_section (destructor)](#dtor)|Destruye una sección crítica.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[lock](#lock)|Adquiere esta sección crítica.|  
|[native_handle](#native_handle)|Devuelve un identificador nativo específico de plataforma, si existe.|  
|[try_lock](#try_lock)|Intenta adquirir el bloqueo sin bloquearse.|  
|[try_lock_for](#try_lock_for)|Intenta adquirir el bloqueo sin bloquearse durante un número específico de milisegundos.|  
|[unlock](#unlock)|Desbloquea la sección crítica.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [estructuras de datos de sincronización](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `critical_section`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>critical_section 

 Construye una nueva sección crítica.  
  
```
critical_section();
```  
  
##  <a name="dtor"></a>~ critical_section 

 Destruye una sección crítica.  
  
```
~critical_section();
```  
  
### <a name="remarks"></a>Comentarios  
 Se espera que ya no se mantiene el bloqueo cuando el destructor se ejecuta. Permitir que la sección crítica se destruya con el bloqueo, sigue dando resultados de comportamiento no definido.  
  
##  <a name="lock"></a>bloqueo 

 Adquiere esta sección crítica.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Comentarios  
 A menudo es más seguro usar la [scoped_lock](#critical_section__scoped_lock_class) construcción para adquirir y liberar un `critical_section` objeto en una excepción forma segura.  
  
 Si el bloqueo ya es retenido por el contexto de llamada, un [improper_lock](improper-lock-class.md) se producirá la excepción.  
  
##  <a name="native_handle"></a>native_handle 

 Devuelve un identificador nativo específico de plataforma, si existe.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la sección crítica.  
  
### <a name="remarks"></a>Comentarios  
 Un `critical_section` objeto no está asociado con un identificador nativo específico de plataforma para el sistema operativo Windows. El método simplemente devuelve una referencia al propio objeto.  
  
##  <a name="critical_section__scoped_lock_class"></a>critical_section:: scoped_lock (clase)  
 Una excepción segura del contenedor RAII para un `critical_section` objeto.  
  
```
class scoped_lock;
```  
  
##  <a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock 

 Construye un `scoped_lock` de objetos y adquiere el `critical_section` objeto pasado en el `_Critical_section` parámetro. Si otro subproceso mantiene la sección crítica, esta llamada se bloqueará.  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Critical_section`  
 La sección crítica para bloquear.  
  
##  <a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock 

 Destruye un `scoped_lock` de objetos y libera la sección crítica proporcionada en su constructor.  
  
```
~scoped_lock();
```  
  
##  <a name="try_lock"></a>try_lock 

 Intenta adquirir el bloqueo sin bloquearse.  
  
```
bool try_lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se adquirió el bloqueo, el valor `true`; en caso contrario, el valor `false`.  
  
##  <a name="try_lock_for"></a>try_lock_for 

 Intenta adquirir el bloqueo sin bloquearse durante un número específico de milisegundos.  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Timeout`  
 El número de milisegundos de espera antes de expirar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se adquirió el bloqueo, el valor `true`; en caso contrario, el valor `false`.  
  
##  <a name="unlock"></a>desbloquear 

 Desbloquea la sección crítica.  
  
```
void unlock();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [reader_writer_lock (clase)](reader-writer-lock-class.md)

