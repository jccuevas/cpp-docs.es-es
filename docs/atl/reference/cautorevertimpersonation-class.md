---
title: Clase CAutoRevertImpersonation | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs: C++
helpviewer_keywords: CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd1d14e73ecc774a8074f47383345d1accc17dc4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|Destruye el objeto y se revierte la suplantación del token de acceso.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](#attach)|Automatiza la reversión de suplantación de un token de acceso.|  
|[CAutoRevertImpersonation::Detach](#detach)|Cancela la reversión de la suplantación automática.|  
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Recupera el actual de token de acceso asociado a este objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Un [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que haya iniciado sesión en un sistema de Windows NT o Windows 2000. Estos tokens de acceso se pueden representar con el `CAccessToken` clase.  
  
 A veces es necesario suplantar los tokens de acceso. Esta clase se proporciona para su comodidad, pero no lleva a cabo la suplantación de tokens de acceso; solo realiza la reversión automática a un estado nonimpersonated. Esto es porque la suplantación del token de acceso puede realizarse de varias maneras diferentes.  
  
 Para obtener una introducción al modelo de control de acceso en Windows, consulte [el Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el SDK de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="attach"></a>CAutoRevertImpersonation::Attach  
 Automatiza la reversión de suplantación de un token de acceso.  
  
```
void Attach(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pAT`  
 La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto para revertir automáticamente  
  
### <a name="remarks"></a>Comentarios  
 Este método solo debe usarse si el [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) objeto se creó con un valor NULL `CAccessToken` puntero, o si [separar](#detach) se llamó anteriormente. En casos sencillos, no es necesario utilizar este método.  
  
##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation  
 Construye un objeto `CAutoRevertImpersonation`.  
  
```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pAT`  
 La dirección de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto para revertir automáticamente.  
  
### <a name="remarks"></a>Comentarios  
 La suplantación del token de acceso real debe realizarse por separado de y, si es posible, antes de la creación de un `CAutoRevertImpersonation` objeto. Esta representación se revertirán automáticamente cuando la `CAutoRevertImpersonation` objeto queda fuera del ámbito.  
  
##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation  
 Destruye el objeto y se revierte la suplantación del token de acceso.  
  
```
~CAutoRevertImpersonation() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Revierte las suplantaciones actualmente en vigor para la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto proporcionado en la construcción o a través del [adjuntar](#attach) método. Si no hay ningún `CAccessToken` está asociado, el destructor no tiene ningún efecto.  
  
##  <a name="detach"></a>CAutoRevertImpersonation::Detach  
 Cancela la reversión de la suplantación automática.  
  
```
const CAccessToken* Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección del asociado previamente [CAccessToken](../../atl/reference/caccesstoken-class.md), o NULL si no existía ninguna asociación.  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a **separar** evita la `CAutoRevertImpersonation` objeto revertir las suplantaciones actualmente en vigor para la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto asociado a este objeto. `CAutoRevertImpersonation`a continuación, se destruye con ningún efecto o reasociar a la misma u otra `CAccessToken` objeto mediante la [adjuntar](#attach).  
  
##  <a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken  
 Recupera el actual de token de acceso asociado a este objeto.  
  
```
const CAccessToken* GetAccessToken() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección del asociado previamente [CAccessToken](../../atl/reference/caccesstoken-class.md), o NULL si no existía ninguna asociación.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a este método para los fines que incluyen la reversión de una suplantación de la `CAccessToken` objeto, el [separar](#detach) método se debería utilizar en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo ATLSecurity](../../visual-cpp-samples.md)   
 [Tokens de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Información general de clases](../../atl/atl-class-overview.md)
