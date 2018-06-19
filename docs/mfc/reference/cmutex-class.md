---
title: Clase CMutex | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d2d68aedaf1d5560c39971e9dd5f74b4492ac6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372465"
---
# <a name="cmutex-class"></a>Clase CMutex
Representa una "exclusión mutua", un objeto de sincronización que permite que un subproceso tenga acceso mutuamente exclusivo a un recurso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|Construye un objeto `CMutex`.|  
  
## <a name="remarks"></a>Comentarios  
 Las exclusiones mutuas son útiles cuando se permita sólo un subproceso a la vez para modificar datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que solo se permiten por un subproceso cada vez. Mediante el uso de un `CMutex` objeto para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.  
  
 Para usar un `CMutex` objeto, construya el `CMutex` objeto cuando sea necesario. Especifique el nombre de la exclusión mutua que se va a esperar y que la aplicación inicialmente debe poseer. A continuación, puede tener acceso a la exclusión mutua cuando devuelve el constructor. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado obtener acceso al recurso controlado.  
  
 Un método alternativo para el uso de `CMutex` objetos consiste en Agregar una variable de tipo `CMutex` como un miembro de datos a la clase que desee controlar. Durante la construcción del objeto controlada, llame al constructor de la `CMutex` miembro de datos que especifica si la exclusión mutua es propiedad inicialmente, el nombre de la exclusión mutua (si se va a utilizar en los límites del proceso) y desea atributos de seguridad.  
  
 Para obtener acceso a recursos controlados por `CMutex` objetos de esta manera, primero cree una variable de cualquier tipo de [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en función de miembro de acceso de los recursos. A continuación, llamar al objeto de bloqueo `Lock` función miembro (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este momento, el subproceso se obtienen acceso al recurso, espere a que el recurso se libera y obtener acceso o esperar a que el recurso se libera y el tiempo de espera, no puede obtener acceso al recurso. En cualquier caso, el recurso se accedió de una manera segura para subprocesos. Para liberar los recursos, utilice el objeto de bloqueo `Unlock` función miembro (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), o permitir que el objeto de bloqueo quede fuera del ámbito.  
  
 Para obtener más información sobre el uso de `CMutex` objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="cmutex"></a>  CMutex::CMutex  
 Construye una con o sin nombre `CMutex` objeto.  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bInitiallyOwn`  
 Especifica si el subproceso que crea el `CMutex` objeto inicialmente tiene acceso al recurso que se controla mediante la exclusión mutua.  
  
 `lpszName`  
 Nombre del objeto `CMutex`. Si existe otro exclusión mutua con el mismo nombre, `lpszName` debe especificarse si el objeto se utilizará en los límites del proceso. Si **NULL**, la exclusión mutua estará sin nombre. Si el nombre coincide con una exclusión mutua existente, el constructor crea un nuevo `CMutex` objeto que hace referencia a la exclusión mutua de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es una exclusión mutua, se producirá un error en la construcción.  
  
 `lpsaAttribute`  
 Atributos de seguridad para el objeto de exclusión mutua. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) del SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener acceso o liberar un `CMutex` , cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llame al método su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones de miembro. Si el `CMutex` se utiliza objeto independiente, llame a su `Unlock` función de miembro para liberarlo.  
  
> [!IMPORTANT]
>  Después de crear el `CMutex` objeto, utilice [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que la exclusión mutua no existía todavía. Si la exclusión mutua existía inesperadamente, puede indicar un proceso rogue es uso inapropiado y puede pretende utilizar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupado por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.  
  
## <a name="see-also"></a>Vea también  
 [CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



