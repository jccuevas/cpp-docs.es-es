---
title: Clase CCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- synchronization objects, critical section
- CCriticalSection class
- critical sections
- synchronization classes, CCriticalSection class
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 25d4b124d089441503e9cb457e648695fc54660d
ms.lasthandoff: 02/24/2017

---
# <a name="ccriticalsection-class"></a>CCriticalSection (clase)
Representa una "sección crítica", un objeto de sincronización que permite que un subproceso cada vez para tener acceso a un recurso o sección de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Construye un objeto `CCriticalSection`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCriticalSection::Lock](#lock)|Usar para obtener acceso a la `CCriticalSection` objeto.|  
|[CCriticalSection::Unlock](#unlock)|Libera el objeto `CCriticalSection`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|Recupera un puntero a interna **CRITICAL_SECTION** objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCriticalSection::m_sect](#m_sect)|Un **CRITICAL_SECTION** objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Las secciones críticas son útiles cuando se permita sólo un subproceso a la vez para modificar datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que sólo se permite un subproceso al mismo tiempo. Mediante el uso de un `CCriticalSection` objeto para controlar la lista vinculada, sólo un subproceso a la vez puede obtener acceso a la lista.  
  
> [!NOTE]
>  La funcionalidad de la `CCriticalSection` clase proporciona un Win32 real **CRITICAL_SECTION** objeto.  
  
 Secciones críticas se utilizan en lugar de las exclusiones mutuas (consulte [CMutex](../../mfc/reference/cmutex-class.md)) cuando la velocidad es fundamental, y el recurso no se utilizará en los límites de proceso.  
  
 Hay dos métodos para utilizar un `CCriticalSection` objeto: independiente y se incrusta en una clase.  
  
-   Método independiente para usar independiente `CCriticalSection` objeto, construir la `CCriticalSection` objeto cuando sea necesario. Después de obtener un valor correcto devuelto desde el constructor, bloquear explícitamente el objeto con una llamada a [bloqueo](#lock). Llamar a [Unlock](#unlock) vez acceso a la sección crítica. Este método, mientras mejor a alguien leer el código fuente, es más propenso a errores, como debe recordar bloquear y desbloquear la sección crítica antes y después de acceso.  
  
     Un método preferible consiste en utilizar el [CSingleLock](../../mfc/reference/csinglelock-class.md) clase. También tiene un `Lock` y `Unlock` (método), pero no tiene que preocuparse por desbloqueando el recurso si se produce una excepción.  
  
-   Incrustado (método) también pueden compartir una clase con varios subprocesos mediante la adición de un `CCriticalSection`-miembro de datos de tipo a la clase y bloquear el miembro de datos cuando sea necesario.  
  
 Para obtener más información sobre el uso de `CCriticalSection` los objetos, vea el artículo [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="a-nameccriticalsectiona--ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>CCriticalSection::CCriticalSection  
 Construye un objeto `CCriticalSection`.  
  
```  
CCriticalSection();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener acceso o liberar una `CCriticalSection` , cree un [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro. Si el `CCriticalSection` objeto se utiliza independiente, llame a su [Unlock](#unlock) función miembro para liberarlo.  
  
 Si el constructor no puede asignar la memoria del sistema requiere, una excepción de memoria (de tipo [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) se inicia automáticamente.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CCriticalSection::Lock](#lock).  
  
##  <a name="a-namelocka--ccriticalsectionlock"></a><a name="lock"></a>CCriticalSection::Lock  
 Llame a esta función miembro para tener acceso al objeto de sección crítica.  
  
```  
BOOL Lock();  
BOOL Lock(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwTimeout`  
 `Lock`omite este valor de parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 `Lock`es una llamada de bloqueo que no regresará hasta que se señaliza el objeto de sección crítica (disponible).  
  
 Si se necesitan esperas cronometradas, puede usar un [CMutex](../../mfc/reference/cmutex-class.md) objeto en lugar de un `CCriticalSection` objeto.  
  
 Si `Lock` no puede asignar la memoria del sistema es necesario, una excepción de memoria (de tipo [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) se inicia automáticamente.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra el enfoque de anidado de sección crítica controlando el acceso a un recurso compartido (estático `_strShared` objeto) con un compartido `CCriticalSection` objeto. El `SomeMethod` función demuestra cómo actualizar un recurso compartido de una manera segura.  
  
 [!code-cpp[NVC_MFC_Utilities&#11;](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]  
  
##  <a name="a-namemsecta--ccriticalsectionmsect"></a><a name="m_sect"></a>CCriticalSection::m_sect  
 Contiene un objeto de sección crítica que se utiliza en todos los `CCriticalSection` métodos.  
  
```  
CRITICAL_SECTION m_sect;  
```  
  
##  <a name="a-nameoperatorcriticalsectionstara--ccriticalsectionoperator-criticalsection"></a><a name="operator_critical_section_star"></a>CCriticalSection::operator CRITICAL_SECTION *  
 Recupera un **CRITICAL_SECTION** objeto.  
  
```  
operator CRITICAL_SECTION*();
```   
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar un puntero al interna **CRITICAL_SECTION** objeto.  
  
##  <a name="a-nameunlocka--ccriticalsectionunlock"></a><a name="unlock"></a>CCriticalSection::Unlock  
 Versiones del `CCriticalSection` objeto para su uso por otro subproceso.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el `CCriticalSection` era propiedad de objeto por el subproceso y la versión se realiza correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el `CCriticalSection` independiente, se está usando `Unlock` se debe llamar inmediatamente después de completar el uso del recurso controlado por la sección crítica. Si un [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto usa, `CCriticalSection::Unlock` será llamado por el objeto de bloqueo `Unlock` función miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CCriticalSection::Lock](#lock).  
  
## <a name="see-also"></a>Vea también  
 [CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CMutex](../../mfc/reference/cmutex-class.md)

