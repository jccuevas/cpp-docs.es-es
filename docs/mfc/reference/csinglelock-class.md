---
title: CSingleLock (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dd07d79c97a9fb3368d20ee68df2332ba7ce5cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="csinglelock-class"></a>CSingleLock (clase)
Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSingleLock  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSingleLock::CSingleLock](#csinglelock)|Construye un objeto `CSingleLock`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSingleLock::IsLocked](#islocked)|Determina si el objeto está bloqueado.|  
|[CSingleLock::Lock](#lock)|Espera a que un objeto de sincronización.|  
|[CSingleLock::Unlock](#unlock)|Libera un objeto de sincronización.|  
  
## <a name="remarks"></a>Comentarios  
 `CSingleLock`no tiene una clase base.  
  
 Para poder utilizar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), y [CEvent](../../mfc/reference/cevent-class.md), debe crear un `CSingleLock` o [CMultiLock](../../mfc/reference/cmultilock-class.md) objeto va a esperar y liberar el objeto de sincronización. Utilice `CSingleLock` cuando sólo deba esperar en un objeto a la vez. Usar **CMultiLock** cuando hay varios objetos que puede usar en un momento determinado.  
  
 Para usar un `CSingleLock` de objeto, llamar a su constructor dentro de una función miembro de clase del recurso controlado. A continuación, llame a la [IsLocked](#islocked) función de miembro para determinar si el recurso está disponible. Si es así, continúe con el resto de la función miembro. Si el recurso no está disponible, espere a que una cantidad especificada de tiempo para el recurso se libera o devolver un error. Una vez completado el uso del recurso, llamar a la [Unlock](#unlock) funcionar si el `CSingleLock` objeto consiste en volver a utilizar o permitir la `CSingleLock` destrucción del objeto.  
  
 `CSingleLock`los objetos requieren la presencia de un objeto derivado de [CSyncObject](../../mfc/reference/csyncobject-class.md). Por lo general, suele ser un miembro de datos de clase del recurso controlado. Para obtener más información sobre cómo usar `CSingleLock` objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CSingleLock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="csinglelock"></a>CSingleLock::CSingleLock  
 Construye un objeto `CSingleLock`.  
  
```  
explicit CSingleLock(
    CSyncObject* pObject,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pObject`  
 Señala al objeto de sincronización para tener acceso. No puede ser **NULL**.  
  
 `bInitialLock`  
 Especifica si se inicialmente intenta tener acceso al objeto proporcionado.  
  
### <a name="remarks"></a>Comentarios  
 Por lo general, esta función se llama desde dentro de una función de miembro de acceso del recurso controlado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>CSingleLock::IsLocked  
 Determina si el objeto asociado con el `CSingleLock` objeto es no señalado (no disponible).  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto está bloqueado; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>CSingleLock::Lock  
 Llame a esta función para obtener acceso a los recursos controlados por el objeto de sincronización proporcionado a la `CSingleLock` constructor.  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwTimeOut*  
 Especifica la cantidad de tiempo de espera para que el objeto de sincronización esté disponible (envía una señal). Si **infinito**, `Lock` esperará hasta que el objeto está señalado antes de devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto de sincronización se señala, `Lock` devolverá correctamente y el subproceso posee ahora el objeto. Si el objeto de sincronización es no señalado (no disponible), `Lock` va a esperar el objeto de sincronización hasta que se señaliza hasta el número de milisegundos especificado en la *dwTimeOut* parámetro. Si no se señaliza el objeto de sincronización en la cantidad especificada de tiempo, `Lock` devuelve el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>CSingleLock::Unlock  
 Libera el objeto de sincronización que pertenecen a `CSingleLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lCount`  
 Número de accesos a la versión. Debe ser mayor que 0. Si la cantidad especificada provocaría que el recuento del objeto supere el máximo, no se cambia el recuento y la función devuelve **FALSE**.  
  
 `lPrevCount`  
 Señala a una variable para recibir el recuento anterior del objeto de sincronización. Si **NULL**, no se devuelve el recuento anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca `CSingleLock`del destructor.  
  
 Si necesita liberar más de un número de intentos de un semáforo, utilice la segunda forma de `Unlock` y especifique el número de accesos a la versión.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMultiLock (clase)](../../mfc/reference/cmultilock-class.md)
