---
title: CDacl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cd66c7c0637b4874f6a40bd77b3387191f00d35
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881206"
---
# <a name="cdacl-class"></a>CDacl (clase)
Esta clase es un contenedor para una estructura DACL (lista de control de acceso discrecional).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CDacl : public CAcl
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDacl::CDacl](#cdacl)|El constructor.|  
|[CDacl::~CDacl](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](#addallowedace)|Agrega una ACE permitida (entrada de control de acceso) a la `CDacl` objeto.|  
|[CDacl::AddDeniedAce](#adddeniedace)|Agrega una ACE denegada para el `CDacl` objeto.|  
|[CDacl::GetAceCount](#getacecount)|Devuelve el número de entradas de control de acceso en el `CDacl` objeto.|  
|[CDacl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) de la `CDacl` objeto.|  
|[CDacl::RemoveAllAces](#removeallaces)|Quita todas las ACE contenidas en el `CDacl` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDacl::operator =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 Descriptor de seguridad de un objeto puede contener una DACL. Una DACL contiene cero o más entradas de control de acceso que identifican los usuarios y grupos que pueden tener acceso al objeto. Si una DACL está vacía (es decir, contiene cero ACE), se concede ningún acceso explícitamente, por lo que implícitamente se deniega el acceso. Sin embargo, si el descriptor de seguridad de un objeto no tiene una DACL, el objeto no está protegido y todo el mundo tiene acceso completo.  
  
 Para recuperar la DACL de un objeto, debe ser el propietario del objeto o tener acceso READ_CONTROL al objeto. Para cambiar la DACL de un objeto, debe tener acceso WRITE_DAC para el objeto.  
  
 Utilice los métodos de clase proporcionados para crear, agregar, quitar y eliminar las ACE de la `CDacl` objeto. Vea también [AtlGetDacl](security-global-functions.md#atlgetdacl) y [AtlSetDacl](security-global-functions.md#atlsetdacl).  
  
 Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el SDK de Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="addallowedace"></a>  CDacl::AddAllowedAce  
 Agrega una ACE permitida (entrada de control de acceso) a la `CDacl` objeto.  
  
```
bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *rSid*  
 Un [CSid](../../atl/reference/csid-class.md) objeto.  
  
 *AccessMask*  
 Especifica la máscara de derechos de acceso para poder ser admitidos para el elemento especificado `CSid` objeto.  
  
 *AceFlags*  
 Un conjunto de marcas de bits que controlan la herencia de la ACE.  
  
 *pObjectType*  
 Tipo del objeto.  
  
 *pInheritedObjectType*  
 El tipo de objeto heredado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la ACE que se agrega a la `CDacl` objeto FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Un `CDacl` objeto contiene cero o más entradas de control de acceso que identifican los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que permita el acceso a la `CDacl` objeto.  
  
 Consulte [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) para obtener una descripción de las diversas marcas que se pueden establecer en el `AceFlags` parámetro.  
  
##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce  
 Agrega una ACE de denegación (entrada de control de acceso) a la `CDacl` objeto.  
  
```
bool AddDeniedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *rSid*  
 Un objeto `CSid`.  
  
 *AccessMask*  
 Especifica la máscara de derechos de acceso será denegado para el elemento especificado `CSid` objeto.  
  
 *AceFlags*  
 Un conjunto de marcas de bits que controlan la herencia de la ACE. El valor predeterminado es 0 en el primer formulario del método.  
  
 *pObjectType*  
 Tipo del objeto.  
  
 *pInheritedObjectType*  
 El tipo de objeto heredado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la ACE que se agrega a la `CDacl` objeto FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Un `CDacl` objeto contiene cero o más entradas de control de acceso que identifican los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que deniega el acceso a la `CDacl` objeto.  
  
 Consulte [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) para obtener una descripción de las diversas marcas que se pueden establecer en el `AceFlags` parámetro.  
  
##  <a name="cdacl"></a>  CDacl::CDacl  
 El constructor.  
  
```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *RHS*  
 Existente `ACL` estructura (lista de control de acceso).  
  
### <a name="remarks"></a>Comentarios  
 El `CDacl` objeto se puede, opcionalmente, crear una existente `ACL` estructura. Es importante tener en cuenta que solo una DACL (lista de control de acceso discrecional) y no una SACL (lista de control de acceso del sistema), se debe pasar como este parámetro. En las compilaciones de depuración, pasando una SACL provocará una aserción. En versiones de lanzamiento, pasando una SACL hará que las entradas de control de acceso en la ACL se omite y se producirá ningún error.  
  
##  <a name="dtor"></a>  CDacl:: ~ CDacl  
 Destructor.  
  
```
~CDacl () throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera los recursos adquiridos por el objeto, incluidas todas las entradas de control de acceso mediante [CDacl::RemoveAllAces](#removeallaces).  
  
##  <a name="getacecount"></a>  CDacl::GetAceCount  
 Devuelve el número de entradas de control de acceso en el `CDacl` objeto.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de ACE contenidos en el `CDacl` objeto.  
  
##  <a name="operator_eq"></a>  CDacl::operator =  
 Operador de asignación.  
  
```
CDacl& operator= (const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *RHS*  
 La ACL (lista de control de acceso) para asignar al objeto existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la actualización `CDacl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que solo pasa una DACL (lista de control de acceso discrecional) a esta función. Pasar una SACL (lista de control de acceso del sistema) a esta función producirá una aserción en las compilaciones de depuración, pero producirá ningún error en las compilaciones de versión.  
  
##  <a name="removeace"></a>  CDacl::RemoveAce  
 Quita una ACE específica (entrada de control de acceso) de la `CDacl` objeto.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nIndex*  
 Índice de la entrada ACE para quitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método se deriva [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>  CDacl::RemoveAllAces  
 Quita todas las entradas de control de acceso contenidas en el `CDacl` objeto.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita cada `ACE` estructura (entrada de control de acceso) (si existe) en el `CDacl` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de seguridad](../../visual-cpp-samples.md)   
 [CAcl (clase)](../../atl/reference/cacl-class.md)   
 [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
