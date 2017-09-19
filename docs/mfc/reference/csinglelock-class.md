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
- CSingleLock class
- threading [MFC], access control
- synchronization objects, access control
- threading [MFC], synchronization
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b1efc2daf1c3714446223cc69f9cc2a6a3401173
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
|[CSingleLock::Lock](#lock)|Se espera un objeto de sincronización.|  
|[CSingleLock::Unlock](#unlock)|Libera un objeto de sincronización.|  
  
## <a name="remarks"></a>Comentarios  
 `CSingleLock`no tiene una clase base.  
  
 Para poder utilizar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), y [CEvent](../../mfc/reference/cevent-class.md), se debe crear un `CSingleLock` o [CMultiLock](../../mfc/reference/cmultilock-class.md) objeto esperar y liberar el objeto de sincronización. Utilice `CSingleLock` cuando sólo deba esperar en un objeto a la vez. Utilice **CMultiLock** cuando hay varios objetos que puede utilizar en un momento determinado.  
  
 Para usar un `CSingleLock` de objeto, llamar a su constructor dentro de una función miembro de clase del recurso controlado. A continuación, llame a la [IsLocked](#islocked) función miembro para determinar si el recurso está disponible. Si lo está, continúe con el resto de la función miembro. Si el recurso no está disponible, espere a que una cantidad especificada de tiempo para el recurso que se libere o devolver el error. Una vez completada la utilización de los recursos, llame a la [Unlock](#unlock) funcionar si el `CSingleLock` objeto es volver a utilizar o permitir la `CSingleLock` destrucción del objeto.  
  
 `CSingleLock`objetos requieren la presencia de un objeto derivado de [CSyncObject](../../mfc/reference/csyncobject-class.md). Por lo general, suele ser un miembro de datos de la clase del recurso controlado. Para obtener más información sobre cómo usar `CSingleLock` los objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
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
 Señala el objeto de sincronización que se tenga acceso. No puede ser **NULL**.  
  
 `bInitialLock`  
 Especifica si se intenta tener acceso al objeto proporcionado inicialmente.  
  
### <a name="remarks"></a>Comentarios  
 Generalmente, esta función se llama desde dentro de una función miembro de acceso del recurso controlado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities Nº&19;](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>CSingleLock::IsLocked  
 Determina si el objeto asociado con el `CSingleLock` objeto es no señalado (no disponible).  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto está bloqueado; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#20;](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>CSingleLock::Lock  
 Llame a esta función para obtener acceso al recurso controlado por el objeto de sincronización proporcionado a la `CSingleLock` constructor.  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwTimeOut*  
 Especifica la cantidad de tiempo de espera para que el objeto de sincronización esté disponible (señalado). Si **infinito**, `Lock` esperará hasta que el objeto está señalado antes de devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto de sincronización se señala, `Lock` devolverá correctamente y ahora, el subproceso propietario del objeto. Si el objeto de sincronización es no señalado (no disponible), `Lock` esperará a que el objeto de sincronización hasta que se señaliza hasta el número de milisegundos especificado en la *dwTimeOut* parámetro. Si el objeto de sincronización no señalará en la cantidad especificada de tiempo, `Lock` devuelve el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFC_Utilities](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
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
 Número de accesos a la versión. Debe ser mayor que 0. Si la cantidad especificada produciría el recuento del objeto supere el máximo, no se cambia el recuento y la función devuelve **FALSE**.  
  
 `lPrevCount`  
 Señala a una variable que recibe el recuento anterior del objeto de sincronización. Si **NULL**, no se devuelve el recuento anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca `CSingleLock`del destructor.  
  
 Si necesita liberar más de un número de acceso de un semáforo, utilice la segunda forma de `Unlock` y especifique el número de accesos a la versión.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFC_Utilities](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CMultiLock (clase)](../../mfc/reference/cmultilock-class.md)

