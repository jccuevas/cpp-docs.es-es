---
title: CComCriticalSection (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5926f92ae636a13c1e5241792790151ee48ceddc
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884875"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection (clase)
Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComCriticalSection
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítica.|  
|[CComCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|  
|[CComCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|  
|[CComCriticalSection::Unlock](#unlock)|Libera la propiedad del objeto de sección crítica.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|Un objeto CRITICAL_SECTION.|  
  
## <a name="remarks"></a>Comentarios  
 `CComCriticalSection` es similar a la clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), salvo que explícitamente se debe inicializar y liberar la sección crítica.  
  
 Normalmente, se utiliza `CComCriticalSection` a través de la **typedef** nombre [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Este nombre hace referencia a `CComCriticalSection` cuando [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) se está usando.  

  
 Consulte [CComCritSecLock (clase)](../../atl/reference/ccomcritseclock-class.md) para una forma más segura de usar esta clase de llamar al `Lock` y `Unlock` directamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection  
 El constructor.  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Establece el [m_sec](#m_sec) miembro de datos en NULL.  
  
##  <a name="init"></a>  CComCriticalSection::Init  
 Llama a la función de Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), que inicializa el objeto de sección crítica contenido en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, E_OUTOFMEMORY o E_FAIL en caso de error.  
  
##  <a name="lock"></a>  CComCriticalSection::Lock  
 Llama a la función de Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), que espera hasta que el subproceso puede tomar posesión del objeto de sección crítica contenida en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, E_OUTOFMEMORY o E_FAIL en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 En primer lugar se debe inicializar el objeto de sección crítica con una llamada a la [Init](#init) método. Cuando el código protegido ha terminado de ejecutarse, el subproceso debe llamar a [Unlock](#unlock) para liberar la propiedad de la sección crítica.  
  
##  <a name="m_sec"></a>  CComCriticalSection::m_sec  
 Contiene un objeto de sección crítica que usen todas `CComCriticalSection` métodos.  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>  CComCriticalSection::Term  
 Llama a la función de Win32 [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), que libera todos los recursos utilizados por el objeto de sección crítica contenido en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Una vez `Term` se ha llamado, críticos sección ya no se puede usar para la sincronización.  
  
##  <a name="unlock"></a>  CComCriticalSection::Unlock  
 Llama a la función de Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), lo que libera la propiedad del objeto de sección crítica contenida en el [m_sec](#m_sec) miembro de datos.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener la propiedad en primer lugar, el subproceso debe llamar a la [bloqueo](#lock) método. Cada llamada a `Lock` requiere una llamada correspondiente a `Unlock` para liberar la propiedad de la sección crítica.  
  
## <a name="see-also"></a>Vea también  
 [CComFakeCriticalSection (clase)](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CComCritSecLock (clase)](../../atl/reference/ccomcritseclock-class.md)
