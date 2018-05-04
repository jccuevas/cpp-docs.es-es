---
title: Clase CComSafeDeleteCriticalSection | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs:
- C++
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cff637f9e307f2714cd351f3c6bcaf1e4b78342e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ccomsafedeletecriticalsection-class"></a>Clase CComSafeDeleteCriticalSection
Esta clase proporciona métodos para la obtención y liberación de propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|El constructor.|  
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítica.|  
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|  
|[CComSafeDeleteCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_bInitialized](#m_binitialized)|Marcas si interno **CRITICAL_SECTION** se ha inicializado el objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComSafeDeleteCriticalSection` deriva de la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin embargo, `CComSafeDeleteCriticalSection` proporciona mecanismos de seguridad adicionales con respecto a [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).  
  
 Cuando una instancia de `CComSafeDeleteCriticalSection` sale del ámbito o explícitamente se elimina de la memoria, el objeto de sección crítica subyacente automáticamente se limpiará si sigue siendo válido. Además, el [CComSafeDeleteCriticalSection::Term](#term) método finalizará correctamente si el objeto de sección crítica subyacente todavía no se ha asignado o ya se ha liberado de la memoria.  
  
 Vea [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre las clases de aplicación auxiliar de sección crítica.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection  
 El constructor.  
  
```
CComSafeDeleteCriticalSection();
```  
  
### <a name="remarks"></a>Comentarios  
 Establece el [m_bInitialized](#m_binitialized) miembro de datos **false**.  
  
##  <a name="dtor"></a>  CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection  
 Destructor.  
  
```
~CComSafeDeleteCriticalSection() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera interno **CRITICAL_SECTION** objeto de la memoria si el [m_bInitialized](#m_binitialized) miembro de datos está establecido en **true**.  
  
##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init  
 Llama a la implementación de la clase base de [Init](/visualstudio/debugger/init) y establece [m_bInitialized](#m_binitialized) a **true** si se realiza correctamente.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).  
  
##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock  
Llama a la implementación de la clase base de [bloqueo](ccomcriticalsection-class.md#lock).  

  
```
HRESULT Lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
### <a name="remarks"></a>Comentarios  
 Este método supone que la [m_bInitialized](#m_binitialized) miembro de datos está establecido en **true** después de la entrada. Si no se cumple esta condición, se genera una aserción en compilaciones de depuración.  
  
 Para obtener más información sobre el comportamiento de la función, consulte [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized  
 Marcas si interno **CRITICAL_SECTION** se ha inicializado el objeto.  
  
```
bool m_bInitialized;
```  
  
### <a name="remarks"></a>Comentarios  
 El **m_bInitialized** miembro de datos se utiliza para realizar un seguimiento de la validez de subyacente **CRITICAL_SECTION** objeto asociado a la [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) clase. Subyacente **CRITICAL_SECTION** objeto no se intentará se libera de la memoria si esta marca no está establecida en **true**.  
  
##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term  
 Llama a la implementación de la clase base de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) si interno **CRITICAL_SECTION** objeto es válido.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), o **S_OK** si [m_bInitialized](#m_binitialized) se estableció en **false** después de la entrada.  
  
### <a name="remarks"></a>Comentarios  
 Es seguro llamar a este aunque método interno **CRITICAL_SECTION** objeto no es válido. El destructor de esta clase llama a este método si el [m_bInitialized](#m_binitialized) miembro de datos está establecido en **true**.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
