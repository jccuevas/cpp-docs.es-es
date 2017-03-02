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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 31de1e553ea2facea6b70c284aecdbf10e22c89f
ms.lasthandoff: 02/24/2017

---
# <a name="csemaphore-class"></a>CSemaphore (clase)
Un objeto de la clase `CSemaphore` representa un "semáforo", un objeto de sincronización que permite que un número limitado de subprocesos de uno o varios procesos tengan acceso a mantener un recuento del número de subprocesos que actualmente tienen acceso a un recurso especificado.  
  
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
 Los semáforos son útiles para controlar el acceso a un recurso compartido que sólo puede admitir un número limitado de usuarios. El recuento actual de la `CSemaphore` objeto es el número de usuarios adicionales permitidos. Cuando el recuento llega a cero, todos los intentos de utilizar el recurso controlado por la **CSemaphore** objeto se inserta en una cola del sistema y espere hasta que finalice cualquier tiempo de espera o el número está por encima de 0. El número máximo de usuarios que pueden tener acceso al recurso controlado en un momento dado se especifica durante la construcción de la `CSemaphore` objeto.  
  
 Para usar un **CSemaphore** objeto, construir la `CSemaphore` objeto cuando sea necesario. Especifique el nombre del semáforo que se va a esperar y que la aplicación inicialmente debe poseer. A continuación, puede tener acceso el semáforo cuando se devuelve el constructor. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando termine teniendo acceso al recurso controlado.  
  
 Un método alternativo para el uso de `CSemaphore` objetos consiste en Agregar una variable de tipo `CSemaphore` como un miembro de datos a la clase que desee controlar. Durante la construcción del objeto controlado, llame al constructor de la `CSemaphore` miembro de datos especifica la inicial acceso recuento, recuento máximo acceso, el nombre del semáforo (si se utilizará en los límites de proceso) y desea los atributos de seguridad.  
  
 Para obtener acceso a los recursos controlados por `CSemaphore` objetos de este modo, primero cree una variable de cualquier tipo de [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en función de miembro de acceso de su recurso. A continuación, llame al objeto de bloqueo `Lock` función miembro (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este punto, el subproceso se obtienen acceso al recurso, espere a que el recurso para liberarse y obtener acceso o espere a que el recurso que se libere y el tiempo de espera, no obtiene acceso al recurso. En cualquier caso, se tiene acceso a los recursos de una manera segura para subprocesos. Para liberar el recurso, utilice el objeto de bloqueo `Unlock` función miembro (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), o permitir que el objeto de bloqueo quedar fuera del ámbito.  
  
 Como alternativa, puede crear un **CSemaphore** objeto independiente y el acceso a él explícitamente antes de intentar tener acceso al recurso controlado. Este método, mientras mejor a alguien leer el código fuente, es más propenso a errores.  
  
 Para obtener más información sobre cómo usar **CSemaphore** los objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="a-namecsemaphorea--csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore::CSemaphore  
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
 El contador de uso máximo del semáforo. Debe ser mayor que 0.  
  
 `pstrName`  
 El nombre del semáforo. Se debe proporcionar si el semáforo se accederá a través de límites de proceso. Si `NULL,` el objeto será sin nombre. Si el nombre coincide con un semáforo existente, el constructor genera una nueva `CSemaphore` objeto que hace referencia el semáforo de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un semáforo, se producirá un error en la construcción.  
  
 *lpsaAttributes*  
 Atributos de seguridad para el objeto de semáforo. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Para obtener acceso o liberar una `CSemaphore` , cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro.  
  
> [!IMPORTANT]
>  Después de crear el `CSemaphore` objeto, utilice [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que la exclusión mutua no existía. Si la exclusión mutua existía inesperadamente, puede indicar un proceso invasor es uso inapropiado y puede prevé utilizar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupados por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.  
  
## <a name="see-also"></a>Vea también  
 [CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




