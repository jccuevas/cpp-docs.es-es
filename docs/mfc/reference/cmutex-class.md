---
title: Clase CMutex | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Mutex
- CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex class
- synchronization classes, CMutex class
- synchronization objects, mutex
- mutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
caps.latest.revision: 22
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
ms.openlocfilehash: 159f2e02dfe44d74ebcaad687a23cef734b61fc9
ms.lasthandoff: 02/24/2017

---
# <a name="cmutex-class"></a>Clase CMutex
Representa una "exclusión mutua", un objeto de sincronización que permite que un subproceso tenga acceso de manera mutuamente exclusivo a un recurso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|Construye un objeto `CMutex`.|  
  
## <a name="remarks"></a>Comentarios  
 Las exclusiones mutuas son útiles cuando se permita sólo un subproceso a la vez para modificar datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que sólo se permite un subproceso al mismo tiempo. Mediante el uso de un `CMutex` objeto para controlar la lista vinculada, sólo un subproceso a la vez puede obtener acceso a la lista.  
  
 Para usar un `CMutex` objeto, construir la `CMutex` objeto cuando sea necesario. Especifique el nombre de la exclusión mutua que se va a esperar y que la aplicación inicialmente debe poseer. A continuación, puede tener acceso a la exclusión mutua cuando se devuelve el constructor. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando termine teniendo acceso al recurso controlado.  
  
 Un método alternativo para el uso de `CMutex` objetos consiste en Agregar una variable de tipo `CMutex` como un miembro de datos a la clase que desee controlar. Durante la construcción del objeto controlado, llame al constructor de la `CMutex` miembro de datos que especifica si la exclusión mutua posee inicialmente, el nombre de la exclusión mutua (si se utilizará en los límites de proceso) y desea los atributos de seguridad.  
  
 Para obtener acceso a los recursos controlados por `CMutex` objetos de este modo, primero cree una variable de cualquier tipo de [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en función de miembro de acceso de su recurso. A continuación, llame al objeto de bloqueo `Lock` función miembro (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este punto, el subproceso se obtienen acceso al recurso, espere a que el recurso para liberarse y obtener acceso o espere a que el recurso que se libere y el tiempo de espera, no obtiene acceso al recurso. En cualquier caso, se tiene acceso a los recursos de una manera segura para subprocesos. Para liberar el recurso, utilice el objeto de bloqueo `Unlock` función miembro (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), o permitir que el objeto de bloqueo quedar fuera del ámbito.  
  
 Para obtener más información sobre el uso de `CMutex` los objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="a-namecmutexa--cmutexcmutex"></a><a name="cmutex"></a>CMutex::CMutex  
 Construye una con o sin nombre `CMutex` objeto.  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bInitiallyOwn`  
 Especifica si el subproceso de creación del `CMutex` objeto inicialmente tiene acceso al recurso controlado por la exclusión mutua.  
  
 `lpszName`  
 Nombre del objeto `CMutex`. Si existe otra exclusión mutua con el mismo nombre, `lpszName` debe especificarse si el objeto se utiliza en los límites de proceso. Si **NULL**, la exclusión mutua estará sin nombre. Si el nombre coincide con una exclusión mutua existente, el constructor genera una nueva `CMutex` objeto que hace referencia a la exclusión mutua de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es una exclusión mutua, se producirá un error en la construcción.  
  
 `lpsaAttribute`  
 Atributos de seguridad para el objeto de exclusión mutua. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Para obtener acceso o liberar una `CMutex` , cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro. Si el `CMutex` objeto se utiliza independiente, llame a su `Unlock` función miembro para liberarlo.  
  
> [!IMPORTANT]
>  Después de crear el `CMutex` objeto, utilice [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que la exclusión mutua no existía. Si la exclusión mutua existía inesperadamente, puede indicar un proceso invasor es uso inapropiado y puede prevé utilizar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupados por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.  
  
## <a name="see-also"></a>Vea también  
 [CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




