---
title: critical_section (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::critical_section
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 20a150c1aedbd9d78c84187bf29e6284a248fbc7
ms.lasthandoff: 02/24/2017

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
|[critical_section (Constructor)](#ctor)|Construye una nueva sección crítica.|  
|[~ critical_section (destructor)](#dtor)|Destruye una sección crítica.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[lock (método)](#lock)|Adquiere esta sección crítica.|  
|[native_handle (método)](#native_handle)|Devuelve un identificador nativo específico de plataforma, si existe.|  
|[try_lock (método)](#try_lock)|Intenta adquirir el bloqueo sin bloquearse.|  
|[try_lock_for (método)](#try_lock_for)|Intenta adquirir el bloqueo sin bloquearse durante un número específico de milisegundos.|  
|[Unlock (método)](#unlock)|Desbloquea la sección crítica.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [estructuras de datos de sincronización](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `critical_section`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namectora-criticalsection"></a><a name="ctor"></a>critical_section 

 Construye una nueva sección crítica.  
  
```
critical_section();
```  
  
##  <a name="a-namedtora-criticalsection"></a><a name="dtor"></a>~ critical_section 

 Destruye una sección crítica.  
  
```
~critical_section();
```  
  
### <a name="remarks"></a>Comentarios  
 Se espera que ya no se mantiene el bloqueo cuando el destructor se ejecuta. Permitir que la sección crítica se destruya con el bloqueo, sigue dando resultados de comportamiento no definido.  
  
##  <a name="a-namelocka-lock"></a><a name="lock"></a>bloqueo 

 Adquiere esta sección crítica.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Comentarios  
 A menudo es más seguro usar la [scoped_lock](#critical_section__scoped_lock_class) construcción para adquirir y liberar un `critical_section` objeto en una excepción forma segura.  
  
 Si el bloqueo ya es retenido por el contexto de llamada, un [improper_lock](improper-lock-class.md) se producirá la excepción.  
  
##  <a name="a-namenativehandlea-nativehandle"></a><a name="native_handle"></a>native_handle 

 Devuelve un identificador nativo específico de plataforma, si existe.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la sección crítica.  
  
### <a name="remarks"></a>Comentarios  
 Un `critical_section` objeto no está asociado con un identificador nativo específico de plataforma para el sistema operativo Windows. El método simplemente devuelve una referencia al propio objeto.  
  
##  <a name="a-namecriticalsectionscopedlockclassa--criticalsectionscopedlock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section:: scoped_lock (clase)  
 Una excepción segura del contenedor RAII para un `critical_section` objeto.  
  
```
class scoped_lock;
```  
  
##  <a name="a-namecriticalsectionscopedlockctora-scopedlockscopedlock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock 

 Construye un `scoped_lock` de objetos y adquiere el `critical_section` objeto pasado en el `_Critical_section` parámetro. Si otro subproceso mantiene la sección crítica, esta llamada se bloqueará.  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Critical_section`  
 La sección crítica para bloquear.  
  
##  <a name="a-namecriticalsectionscopedlockdtora-scopedlockscopedlock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock 

 Destruye un `scoped_lock` de objetos y libera la sección crítica proporcionada en su constructor.  
  
```
~scoped_lock();
```  
  
##  <a name="a-nametrylocka-trylock"></a><a name="try_lock"></a>try_lock 

 Intenta adquirir el bloqueo sin bloquearse.  
  
```
bool try_lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se adquirió el bloqueo, el valor `true`; en caso contrario, el valor `false`.  
  
##  <a name="a-nametrylockfora-trylockfor"></a><a name="try_lock_for"></a>try_lock_for 

 Intenta adquirir el bloqueo sin bloquearse durante un número específico de milisegundos.  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Timeout`  
 El número de milisegundos de espera antes de expirar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se adquirió el bloqueo, el valor `true`; en caso contrario, el valor `false`.  
  
##  <a name="a-nameunlocka-unlock"></a><a name="unlock"></a>desbloquear 

 Desbloquea la sección crítica.  
  
```
void unlock();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [reader_writer_lock (clase)](reader-writer-lock-class.md)

