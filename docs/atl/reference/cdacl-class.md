---
title: Clase CDacl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDacl
- CDacl
- ATL.CDacl
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
caps.latest.revision: 23
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
ms.openlocfilehash: bb418919c26e3c0054a151b859cdf3f31c5d73a8
ms.lasthandoff: 02/24/2017

---
# <a name="cdacl-class"></a>Clase CDacl
Esta clase es un contenedor para una estructura DACL (lista de control de acceso discrecional).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CDacl : public CAcl
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDacl::CDacl](#cdacl)|El constructor.|  
|[CDacl:: ~ CDacl](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](#addallowedace)|Agrega una ACE permitida (entrada de control de acceso) a la `CDacl` objeto.|  
|[CDacl::AddDeniedAce](#adddeniedace)|Agrega una ACE denegada la `CDacl` objeto.|  
|[CDacl::GetAceCount](#getacecount)|Devuelve el número de entradas de control de acceso en la `CDacl` objeto.|  
|[CDacl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) de la `CDacl` objeto.|  
|[CDacl::RemoveAllAces](#removeallaces)|Quita todas las ACE contenidas en el `CDacl` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDacl::operator =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 Descriptor de seguridad de un objeto puede contener una DACL. Una DACL contiene cero o más entradas de control de acceso que identifican los usuarios y grupos que pueden tener acceso al objeto. Si una DACL está vacía (es decir, contiene cero ACE), se concede ningún acceso explícitamente, por lo que el acceso se deniega implícitamente. Sin embargo, si el descriptor de seguridad de un objeto no tiene una DACL, el objeto no está protegido y todo el mundo tiene acceso completo.  
  
 Para recuperar la DACL de un objeto, debe ser el propietario del objeto o tener acceso READ_CONTROL al objeto. Para cambiar la DACL de un objeto, debe tener acceso WRITE_DAC para el objeto.  
  
 Utilice los métodos de clase proporcionados para crear, agregar, quitar y eliminar las ACE de la `CDacl` objeto. Consulte también [AtlGetDacl](http://msdn.microsoft.com/library/a0973648-0d46-4c1a-914f-bda861fe5d19) y [AtlSetDacl](http://msdn.microsoft.com/library/eb88ccb6-1f1b-444d-b0c9-8d5cd0dd6c0b).  
  
 Para obtener una introducción al modelo de control de acceso de Windows, consulte [de Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="a-nameaddallowedacea--cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::AddAllowedAce  
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
 `rSid`  
 Un [CSid](../../atl/reference/csid-class.md) objeto.  
  
 `AccessMask`  
 Especifica la máscara de derechos de acceso que se permitan especificado `CSid` objeto.  
  
 `AceFlags`  
 Un conjunto de marcadores de bits que controlan la herencia de la ACE.  
  
 `pObjectType`  
 Tipo del objeto.  
  
 `pInheritedObjectType`  
 El tipo de objeto heredado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la ACE se agrega a la `CDacl` objeto, **false** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Un `CDacl` objeto contiene cero o más entradas de control de acceso que identifican los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que permite el acceso a la `CDacl` objeto.  
  
> [!NOTE]
>  La segunda forma de `AddAllowedAce` sólo está disponible en Windows 2000 y versiones posteriores.  
  
 Consulte [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) para obtener una descripción de los distintos indicadores que se puede establecer en el `AceFlags` parámetro.  
  
##  <a name="a-nameadddeniedacea--cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::AddDeniedAce  
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
 `rSid`  
 Objeto `CSid`.  
  
 `AccessMask`  
 Especifica la máscara de derechos de acceso que se deniegan especificado `CSid` objeto.  
  
 `AceFlags`  
 Un conjunto de marcadores de bits que controlan la herencia de la ACE. El valor predeterminado es 0 en la primera forma del método.  
  
 `pObjectType`  
 Tipo del objeto.  
  
 `pInheritedObjectType`  
 El tipo de objeto heredado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la ACE se agrega a la `CDacl` objeto, **false** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Un `CDacl` objeto contiene cero o más entradas de control de acceso que identifican los usuarios y grupos que pueden tener acceso al objeto. Este método agrega una ACE que deniega el acceso a la `CDacl` objeto.  
  
> [!NOTE]
>  La segunda forma de `AddDeniedAce` sólo está disponible en Windows 2000 y versiones posteriores.  
  
 Consulte [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) para obtener una descripción de los distintos indicadores que se puede establecer en el `AceFlags` parámetro.  
  
##  <a name="a-namecdacla--cdaclcdacl"></a><a name="cdacl"></a>CDacl::CDacl  
 El constructor.  
  
```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 Existente **ACL** estructura (lista de control de acceso).  
  
### <a name="remarks"></a>Comentarios  
 El `CDacl` objeto puede crearse opcionalmente mediante existente **ACL** estructura. Es importante tener en cuenta que sólo una DACL (lista de control de acceso discrecional), y no una SACL (lista de control de acceso del sistema), se debe pasar como este parámetro. En compilaciones de depuración, pasando una SACL provocará una aserción. En versiones de lanzamiento, pasando una SACL hará que las entradas de control de acceso en la ACL se omite y se producirá ningún error.  
  
##  <a name="a-namedtora--cdaclcdacl"></a><a name="dtor"></a>CDacl:: ~ CDacl  
 Destructor.  
  
```
~CDacl () throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera los recursos adquiridos por el objeto, incluidas todas las entradas de control de acceso mediante [CDacl::RemoveAllAces](#removeallaces).  
  
##  <a name="a-namegetacecounta--cdaclgetacecount"></a><a name="getacecount"></a>CDacl::GetAceCount  
 Devuelve el número de entradas de control de acceso en la `CDacl` objeto.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de ACE contenida en el `CDacl` objeto.  
  
##  <a name="a-nameoperatoreqa--cdacloperator-"></a><a name="operator_eq"></a>CDacl::operator =  
 Operador de asignación.  
  
```
CDacl& operator= (const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 ACL (lista de control de acceso) para asignar al objeto existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la actualización `CDacl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que sólo se pasa una DACL (lista de control de acceso discrecional) a esta función. Pasar una SACL (lista de control de acceso del sistema) a esta función producirá una aserción en compilaciones de depuración, pero producirá ningún error en las versiones de lanzamiento.  
  
##  <a name="a-nameremoveacea--cdaclremoveace"></a><a name="removeace"></a>CDacl::RemoveAce  
 Quita una ACE específica (entrada de control de acceso) de la `CDacl` objeto.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de la entrada ACE que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método se deriva [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="a-nameremoveallacesa--cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::RemoveAllAces  
 Quita todas las entradas de control de acceso contenidas en el `CDacl` objeto.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita cada **ACE** (estructura) (entrada de control de acceso) (si existe) en el `CDacl` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de seguridad](../../visual-cpp-samples.md)   
 [Clase CAcl](../../atl/reference/cacl-class.md)   
 [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)

