---
title: CMultiLock (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiLock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock class
- synchronization objects, access control
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: 20
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: a58d59d8e4d7a1c542dee80295dd8eef6c8be338
ms.lasthandoff: 02/24/2017

---
# <a name="cmultilock-class"></a>CMultiLock (clase)
Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMultiLock  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMultiLock::CMultiLock](#cmultilock)|Construye un objeto `CMultiLock`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMultiLock::IsLocked](#islocked)|Determina si un objeto de sincronización específica de la matriz está bloqueado.|  
|[CMultiLock::Lock](#lock)|Espera en la matriz de objetos de sincronización.|  
|[CMultiLock::Unlock](#unlock)|Libera todos los objetos propiedad de sincronización.|  
  
## <a name="remarks"></a>Comentarios  
 `CMultiLock`no tiene una clase base.  
  
 Utilizar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), y [CEvent](../../mfc/reference/cevent-class.md), puede crear un **CMultiLock** o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto esperar y liberar el objeto de sincronización. Utilice **CMultiLock** cuando hay varios objetos que puede utilizar en un momento determinado. Utilice `CSingleLock` cuando sólo deba esperar en un objeto a la vez.  
  
 Para usar un **CMultiLock** , cree primero una matriz de los objetos de sincronización que se va a esperar. A continuación, llame el **CMultiLock** constructor del objeto dentro de una función miembro de clase del recurso controlado. A continuación, llame a la [bloqueo](#lock) función miembro para determinar si un recurso está disponible (señalado). Si hay alguno, continúe con el resto de la función miembro. Si ningún recurso está disponible, espere a que una cantidad especificada de tiempo para un recurso que se libere o devolver el error. Una vez finalizado el uso de un recurso, llame a la [Unlock](#unlock) funcionar si el **CMultiLock** objeto es volver a utilizar o permitir la **CMultiLock** destrucción del objeto.  
  
 **CMultiLock** objetos son muy útiles cuando un subproceso tiene un gran número de `CEvent` puede responder a los objetos. Crear una matriz que contiene todos los `CEvent` punteros y llamar a `Lock`. Esto hará que el subproceso espere hasta que se señaliza uno de los eventos.  
  
 Para obtener más información sobre cómo usar **CMultiLock** los objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CMultiLock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="a-namecmultilocka--cmultilockcmultilock"></a><a name="cmultilock"></a>CMultiLock::CMultiLock  
 Construye un **CMultiLock** objeto.  
  
```  
CMultiLock(
    CSyncObject* ppObjects [ ],  
    DWORD dwCount,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppObjects`  
 Matriz de punteros a los objetos de sincronización al que se espera. No puede ser **NULL**.  
  
 `dwCount`  
 Número de objetos de `ppObjects`. Debe ser mayor que 0.  
  
 `bInitialLock`  
 Especifica si se intenta tener acceso a cualquiera de los objetos proporcionados inicialmente.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca después de crear la matriz de objetos de sincronización al que se espera. Normalmente se llama desde dentro del subproceso que se debe esperar a que uno de los objetos de sincronización esté disponible.  
  
##  <a name="a-nameislockeda--cmultilockislocked"></a><a name="islocked"></a>CMultiLock::IsLocked  
 Determina si el objeto especificado es no señalado (no disponible).  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwItem*  
 Índice de la matriz de objetos correspondiente al objeto cuyo estado se va a consultar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto especificado está bloqueado; en caso contrario, 0.  
  
##  <a name="a-namelocka--cmultilocklock"></a><a name="lock"></a>CMultiLock::Lock  
 Llame a esta función para obtener acceso a uno o varios de los recursos controlados por los objetos de sincronización proporcionados para la **CMultiLock** constructor.  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwTimeOut*  
 Especifica la cantidad de tiempo de espera para que el objeto de sincronización esté disponible (señalado). Si **infinito**, `Lock` esperará hasta que el objeto está señalado antes de devolver.  
  
 `bWaitForAll`  
 Especifica si todos los objetos de espera en deben señalarse al mismo tiempo antes de devolver. Si **FALSE**, `Lock` devolverá cuando se señala a cualquiera de los objetos de espera.  
  
 `dwWakeMask`  
 Especifica otras condiciones que pueden anular la espera. Para obtener una lista completa de las opciones disponibles para este parámetro, consulte [MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Si `Lock` se produce un error, devuelve – 1. Si se realiza correctamente, devuelve uno de los siguientes valores:  
  
-   Entre **WAIT_OBJECT_0** y **WAIT_OBJECT_0** + (número de objetos: 1)  
  
     Si `bWaitForAll` es **TRUE**, todos los objetos se señalizan (disponible). Si `bWaitForAll` es **FALSE**, el valor devuelto: **WAIT_OBJECT_0** es el índice de la matriz de objetos del objeto que se señala (disponible).  
  
- **WAIT_OBJECT_0** + (número de objetos)  
  
     Un evento especificado en `dwWakeMask` está disponible en la cola de entrada del subproceso.  
  
-   Entre **WAIT_ABANDONED_0** y **WAIT_ABANDONED_0** + (número de objetos: 1)  
  
     Si `bWaitForAll` es **TRUE**, se marcan todos los objetos y al menos uno de los objetos es un objeto de exclusión mutua abandonada. Si `bWaitForAll` es **FALSE**, el valor devuelto: **WAIT_ABANDONED_0** es el índice de la matriz de objetos del objeto mutex abandonado que satisfizo la espera.  
  
- **WAIT_TIMEOUT**  
  
     El intervalo de tiempo de espera especificado en *dwTimeOut* caducado sin espera subsiguientes.  
  
### <a name="remarks"></a>Comentarios  
 Si `bWaitForAll` es **TRUE**, `Lock` devolverá correctamente tan pronto como todos los objetos de sincronización se señalen al mismo tiempo. Si `bWaitForAll` es **FALSE**, `Lock` devolverá en cuanto se señalen uno o varios de los objetos de sincronización.  
  
 Si `Lock` no es capaz de devolver inmediatamente, esperará que no supere el número de milisegundos especificado en la *dwTimeOut* parámetro antes de devolver. Si *dwTimeOut* es **infinito**, `Lock` , no se devolverá hasta que se obtiene acceso a un objeto o una condición especificada en `dwWakeMask` se cumplió. De lo contrario, si `Lock` era capaz de adquirir un objeto de sincronización, devolverá correctamente; si no, devolverán un error.  
  
##  <a name="a-nameunlocka--cmultilockunlock"></a><a name="unlock"></a>CMultiLock::Unlock  
 Libera el objeto de sincronización que pertenecen a `CMultiLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lCount`  
 Cuenta el número de referencia para la versión. Debe ser mayor que 0. Si la cantidad especificada produciría el recuento del objeto supere el máximo, no se cambia el recuento y la función devuelve **FALSE**.  
  
 `lPrevCount`  
 Señala a una variable que recibe el recuento anterior para el objeto de sincronización. Si **NULL**, no se devuelve el recuento anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca `CMultiLock`del destructor.  
  
 La primera forma de `Unlock` intenta desbloquear el objeto de sincronización administrado por `CMultiLock`. La segunda forma de `Unlock` intenta desbloquear el `CSemaphore` objetos que pertenecen a `CMultiLock`. Si `CMultiLock` no posee cualquiera bloqueado `CSemaphore` de objeto, la función devuelve **FALSE**; en caso contrario, devuelve **TRUE**. `lCount`y `lpPrevCount` son exactamente los mismos que los parámetros de [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). La segunda forma de `Unlock` es rara vez aplicable a situaciones multilock.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




