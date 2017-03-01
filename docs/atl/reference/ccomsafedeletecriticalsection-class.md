---
title: Clase CComSafeDeleteCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATL::CComSafeDeleteCriticalSection
- ATL.CComSafeDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: 18
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 511627de9d4f6411c508dd78a237cf546e2493de
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsafedeletecriticalsection-class"></a>Clase CComSafeDeleteCriticalSection
Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|El constructor.|  
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](#init)|Crea e inicializa un objeto de sección crítica.|  
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtiene la propiedad del objeto de sección crítica.|  
|[CComSafeDeleteCriticalSection::Term](#term)|Libera los recursos del sistema utilizados por el objeto de sección crítica.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_bInitialized](#m_binitialized)|Marcas si interna **CRITICAL_SECTION** se ha inicializado el objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComSafeDeleteCriticalSection`deriva de la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin embargo, `CComSafeDeleteCriticalSection` proporciona mecanismos de seguridad adicional sobre [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).  
  
 Cuando una instancia de `CComSafeDeleteCriticalSection` sale del ámbito o explícitamente se elimina de la memoria, el objeto de sección crítica subyacente automáticamente se limpiará si aún es válido. Además, el [CComSafeDeleteCriticalSection::Term](#term) método se cerrará correctamente si el objeto de sección crítica subyacente no se ha asignado o ya se ha liberado de la memoria.  
  
 Consulte [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre las clases auxiliares de sección crítica.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="a-nameccomsafedeletecriticalsectiona--ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection  
 El constructor.  
  
```
CComSafeDeleteCriticalSection();
```  
  
### <a name="remarks"></a>Comentarios  
 Establece la [m_bInitialized](#m_binitialized) miembro de datos **false**.  
  
##  <a name="a-namedtora--ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection  
 Destructor.  
  
```
~CComSafeDeleteCriticalSection() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera el interno **CRITICAL_SECTION** objeto de la memoria si el [m_bInitialized](#m_binitialized) miembro de datos está establecido en **true**.  
  
##  <a name="a-nameinita--ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafeDeleteCriticalSection::Init  
 Llama a la implementación de la clase base de [Init](/visualstudio/debugger/init) y establece [m_bInitialized](#m_binitialized) a **true** si se realiza correctamente.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).  
  
##  <a name="a-namelocka--ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafeDeleteCriticalSection::Lock  
Llama a la implementación de la clase base de [bloqueo](ccomcriticalsection-class.md#lock).  

  
```
HRESULT Lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
### <a name="remarks"></a>Comentarios  
 Este método supone la [m_bInitialized](#m_binitialized) miembro de datos está establecido en **true** tras su entrada. Si no se cumple esta condición, se genera una aserción en compilaciones de depuración.  
  
 Para obtener más información sobre el comportamiento de la función, consulte [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
##  <a name="a-namembinitializeda--ccomsafedeletecriticalsectionmbinitialized"></a><a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized  
 Marcas si interna **CRITICAL_SECTION** se ha inicializado el objeto.  
  
```
bool m_bInitialized;
```  
  
### <a name="remarks"></a>Comentarios  
 El **m_bInitialized** miembro de datos se utiliza para realizar un seguimiento de la validez de la base de **CRITICAL_SECTION** objeto asociado a la [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) clase. Subyacente **CRITICAL_SECTION** objeto no se intentará liberar de memoria si no se establece esta marca en **true**.  
  
##  <a name="a-nameterma--ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafeDeleteCriticalSection::Term  
 Llama a la implementación de la clase base de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) si interna **CRITICAL_SECTION** objeto es válido.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), o **S_OK** si [m_bInitialized](#m_binitialized) se estableció en **false** tras su entrada.  
  
### <a name="remarks"></a>Comentarios  
 Es seguro llamar a este aunque método interno **CRITICAL_SECTION** objeto no es válido. El destructor de esta clase llama a este método si el [m_bInitialized](#m_binitialized) miembro de datos está establecido en **true**.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

