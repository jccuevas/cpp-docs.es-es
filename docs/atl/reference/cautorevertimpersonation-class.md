---
title: Clase CAutoRevertImpersonation | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs:
- C++
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: f86f1e5067583b3c4c615c8ca3095e8b67b3fffe
ms.lasthandoff: 02/24/2017

---
# <a name="cautorevertimpersonation-class"></a>Clase CAutoRevertImpersonation
Esta clase revierte [CAccessToken](../../atl/reference/caccesstoken-class.md) objetos a un estado nonimpersonating cuando sale del ámbito.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAutoRevertImpersonation
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Construye un `CAutoRevertImpersonation` objeto|  
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|Destruye el objeto y revierte la suplantación del token de acceso.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](#attach)|Automatiza la reversión de la suplantación de un token de acceso.|  
|[CAutoRevertImpersonation::Detach](#detach)|Cancela la reversión de la suplantación automática.|  
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Recupera actual de token de acceso asociado a este objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Un [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows NT o Windows 2000. Estos tokens de acceso se pueden representar con el `CAccessToken` clase.  
  
 A veces es necesario suplantar los tokens de acceso. Esta clase se proporciona por comodidad, pero no realiza la suplantación de tokens de acceso; sólo se realiza la reversión automática a un estado nonimpersonated. Esto es porque la suplantación del token de acceso puede realizarse de varias maneras diferentes.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, consulte [de Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="attach"></a>CAutoRevertImpersonation::Attach  
 Automatiza la reversión de la suplantación de un token de acceso.  
  
```
void Attach(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pAT`  
 La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto se revierten automáticamente  
  
### <a name="remarks"></a>Comentarios  
 Este método sólo debe utilizarse si la [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) objeto creado con un valor NULL `CAccessToken` puntero, o si [separar](#detach) se llamó anteriormente. En los casos, no es necesario utilizar este método.  
  
##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation  
 Construye un objeto `CAutoRevertImpersonation`.  
  
```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pAT`  
 La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto se revierten automáticamente.  
  
### <a name="remarks"></a>Comentarios  
 La representación real del token de acceso debe realizarse por separado desde y preferentemente antes de la creación de un `CAutoRevertImpersonation` objeto. Esta representación se revertirán automáticamente cuando la `CAutoRevertImpersonation` objeto sale del ámbito.  
  
##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation  
 Destruye el objeto y revierte la suplantación del token de acceso.  
  
```
~CAutoRevertImpersonation() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Revierte cualquier suplantación actualmente en vigor para la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto proporcionado en la construcción o a través del [adjuntar](#attach) método. Si no hay ningún `CAccessToken` está asociado, el destructor no tiene ningún efecto.  
  
##  <a name="detach"></a>CAutoRevertImpersonation::Detach  
 Cancela la reversión de la suplantación automática.  
  
```
const CAccessToken* Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección del asociado previamente [CAccessToken](../../atl/reference/caccesstoken-class.md), o NULL si no existía ninguna asociación.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a **separar** evita el `CAutoRevertImpersonation` objeto revertir la suplantación actualmente en vigor para la [CAccessToken](../../atl/reference/caccesstoken-class.md) asociado a este objeto. `CAutoRevertImpersonation`puede destruir con ningún efecto o vuelto a asociar a la misma u otra `CAccessToken` objeto mediante [adjuntar](#attach).  
  
##  <a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken  
 Recupera actual de token de acceso asociado a este objeto.  
  
```
const CAccessToken* GetAccessToken() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección del asociado previamente [CAccessToken](../../atl/reference/caccesstoken-class.md), o NULL si no existía ninguna asociación.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a este método para los fines que incluyen la reversión de una suplantación de la `CAccessToken` objeto, el [separar](#detach) método se debe utilizar en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo ATLSecurity](../../visual-cpp-samples.md)   
 [Tokens de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Información general de la clase](../../atl/atl-class-overview.md)

