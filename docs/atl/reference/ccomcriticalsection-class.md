---
title: Clase CComCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
dev_langs:
- C++
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: a7c4fbc87ff06bb09766eb3e4ad0d7c5275eed65
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcriticalsection-class"></a>Clase CComCriticalSection
Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComCriticalSection
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítica.|  
|[CComCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|  
|[CComCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|  
|[CComCriticalSection::Unlock](#unlock)|Libera la propiedad del objeto de sección crítica.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|Un **CRITICAL_SECTION** objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComCriticalSection`es similar a la clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), salvo que explícitamente se debe inicializar y liberar la sección crítica.  
  
 Normalmente, se utiliza `CComCriticalSection` a través de la `typedef` nombre [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Este nombre hace referencia a `CComCriticalSection` cuando [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) se está usando.  

  
 Consulte [CComCritSecLock clase](../../atl/reference/ccomcritseclock-class.md) de una forma más segura de usar esta clase de llamada `Lock` y `Unlock` directamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection  
 El constructor.  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Establece la [m_sec](#m_sec) miembro de datos NULL **.**  
  
##  <a name="init"></a>CComCriticalSection::Init  
 Llama a la función de Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), que inicializa el objeto de sección crítica contenido en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` correctamente, **E_OUTOFMEMORY** o **E_FAIL** en caso de error.  
  
##  <a name="lock"></a>CComCriticalSection::Lock  
 Llama a la función de Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), que espera hasta que el subproceso puede tomar posesión del objeto de sección crítica contenida en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` correctamente, **E_OUTOFMEMORY** o **E_FAIL** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Primero se debe inicializar el objeto de sección crítica con una llamada a la [Init](#init) método. Cuando el código protegido ha terminado de ejecutarse, el subproceso debe llamar a [Unlock](#unlock) para liberar la propiedad de la sección crítica.  
  
##  <a name="m_sec"></a>CComCriticalSection::m_sec  
 Contiene un objeto de sección crítica que se utiliza en todos los `CComCriticalSection` métodos.  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>CComCriticalSection::Term  
 Llama a la función de Win32 [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), que libera todos los recursos utilizados por el objeto de sección crítica contenido en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Una vez `Term` se ha llamado, críticos sección ya no se puede utilizar para la sincronización.  
  
##  <a name="unlock"></a>CComCriticalSection::Unlock  
 Llama a la función de Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), lo que libera la propiedad del objeto de sección crítica contenida en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener la propiedad en primer lugar, el subproceso debe llamar a la [bloqueo](#lock) método. Cada llamada a `Lock` requiere una llamada correspondiente a `Unlock` para liberar la propiedad de la sección crítica.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clase CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)

