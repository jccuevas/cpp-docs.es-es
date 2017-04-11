---
title: CSemaphore (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs:
- C++
helpviewer_keywords:
- synchronization objects, semaphores
- CSemaphore class
- semaphores
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 811510bab51ab7909b90b52247d34b71dda5b961
ms.lasthandoff: 04/04/2017

---
# <a name="csemaphore-class"></a>CSemaphore (clase)
Un objeto de clase `CSemaphore` representa un "semáforo", un objeto de sincronización que permite un número limitado de subprocesos de uno o varios procesos tengan acceso a mantener un recuento del número de subprocesos que acceden actualmente a un recurso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](#csemaphore)|Construye un objeto `CSemaphore`.|  
  
## <a name="remarks"></a>Comentarios  
 Semáforos son útiles para controlar el acceso a un recurso compartido al que sólo puede admitir un número limitado de usuarios. El recuento actual de la `CSemaphore` objeto es el número de usuarios adicionales permitidos. Cuando el recuento llega a cero, todos los intentos de utilizar el recurso controlado por la **CSemaphore** objeto se insertará en una cola del sistema y espere hasta que finalice cualquier tiempo de espera o el número está por encima de 0. El número máximo de usuarios que pueden tener acceso al recurso controlado al mismo tiempo que se especifica durante la construcción de la `CSemaphore` objeto.  
  
 Para usar un **CSemaphore** objeto, construya el `CSemaphore` objeto cuando sea necesario. Especifique el nombre del semáforo que se va a esperar y que la aplicación inicialmente debe poseer. A continuación, puede tener acceso el semáforo cuando se devuelve el constructor. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado obtener acceso al recurso controlado.  
  
 Un método alternativo para el uso de `CSemaphore` objetos consiste en Agregar una variable de tipo `CSemaphore` como un miembro de datos a la clase que desee controlar. Durante la construcción del objeto controlada, llame al constructor de la `CSemaphore` miembro de datos especifica la inicial de acceso recuento, recuento máximo de acceso y nombre del semáforo (si se va a utilizar en los límites del proceso) y desea atributos de seguridad.  
  
 Para obtener acceso a recursos controlados por `CSemaphore` objetos de esta manera, primero cree una variable de cualquier tipo de [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en función de miembro de acceso de los recursos. A continuación, llamar al objeto de bloqueo `Lock` función miembro (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este momento, el subproceso se obtienen acceso al recurso, espere a que el recurso se libera y obtener acceso o esperar a que el recurso se libera y el tiempo de espera, no puede obtener acceso al recurso. En cualquier caso, el recurso se accedió de una manera segura para subprocesos. Para liberar los recursos, utilice el objeto de bloqueo `Unlock` función miembro (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), o permitir que el objeto de bloqueo quede fuera del ámbito.  
  
 Como alternativa, puede crear un **CSemaphore** objeto independiente y acceso a él explícitamente antes de intentar tener acceso al recurso controlado. Este método, al mejor a alguien leer el código fuente, es más propenso a errores.  
  
 Para obtener más información sobre cómo usar **CSemaphore** objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="csemaphore"></a>CSemaphore::CSemaphore  
 Construye una con o sin nombre `CSemaphore` objeto.  
  
```  
CSemaphore(
    LONG lInitialCount = 1,  
    LONG lMaxCount = 1,  
    LPCTSTR pstrName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *lInitialCount*  
 El contador de uso inicial para el semáforo. Debe ser mayor o igual a 0 y menor o igual que `lMaxCount`.  
  
 `lMaxCount`  
 El contador de uso máximo para el semáforo. Debe ser mayor que 0.  
  
 `pstrName`  
 El nombre del semáforo. Debe especificarse si el semáforo se accederá a través de límites de proceso. Si `NULL`, el objeto será sin nombre. Si el nombre coincide con un semáforo existente, el constructor crea un nuevo `CSemaphore` objeto que hace referencia el semáforo de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un semáforo, se producirá un error en la construcción.  
  
 *lpsaAttributes*  
 Atributos de seguridad para el objeto de semáforo. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Para obtener acceso o liberar un `CSemaphore` de objetos, crear un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llame al método su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro.  
  
> [!IMPORTANT]
>  Después de crear el `CSemaphore` objeto, utilice [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que la exclusión mutua no existía todavía. Si la exclusión mutua existía inesperadamente, puede indicar un proceso rogue es uso inapropiado y puede pretende utilizar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupado por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.  
  
## <a name="see-also"></a>Vea también  
 [CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)




