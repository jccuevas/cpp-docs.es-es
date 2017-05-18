---
title: Clase CSacl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: bd9ef9932938cfe5ec65965b3a40116da7f43b90
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="csacl-class"></a>Clase CSacl
Esta clase es un contenedor para una estructura SACL (lista de control de acceso del sistema).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|El constructor.|  
|[CSacl:: ~ CSacl](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|Agrega una entrada de control de acceso (ACE) de auditoría a la `CSacl` objeto.|  
|[CSacl::GetAceCount](#getacecount)|Devuelve el número de entradas de control de acceso (ACE) en el `CSacl` objeto.|  
|[CSacl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) de la **CSacl** objeto.|  
|[CSacl::RemoveAllAces](#removeallaces)|Quita todas las entradas de ACE contenidos en la `CSacl` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 Una SACL contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan registros de auditoría en el registro de eventos de seguridad de un controlador de dominio. Tenga en cuenta que una SACL genera las entradas del registro sólo en el controlador de dominio donde se produjo el intento de acceso, no en cada controlador de dominio que contiene una réplica del objeto.  
  
 Para establecer o recuperar la SACL del descriptor de seguridad de un objeto, el privilegio SE_SECURITY_NAME debe estar habilitado en el token de acceso del subproceso que lo solicitado. El grupo Administradores tiene este permiso concede de forma predeterminada, y se pueden conceder a otros usuarios o grupos. Tener el privilegio concedido no es todo lo necesario: para poder realizar la operación definida por el privilegio, el privilegio debe estar habilitado en el token de acceso de seguridad para que surta efecto. El modelo permite privilegios habilitarse únicamente para las operaciones de sistema específico y, a continuación, se deshabilitan cuando ya no son necesarios. Vea [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl) para obtener ejemplos de cómo habilitar SE_SECURITY_NAME.  
  
 Utilice los métodos de clase proporcionados para agregar, quitar, crear y eliminar ACE de la **SACL** objeto. Vea también [AtlGetSacl](security-global-functions.md#atlgetsacl) y [AtlSetSacl](security-global-functions.md#atlsetsacl).  
  
 Para obtener una introducción al modelo de control de acceso en Windows, consulte [el Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="addauditace"></a>CSacl::AddAuditAce  
 Agrega una entrada de control de acceso (ACE) de auditoría a la `CSacl` objeto.  
  
```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 El [CSid](../../atl/reference/csid-class.md) objeto.  
  
 `AccessMask`  
 Especifica la máscara de derechos de acceso que se auditarán para el elemento especificado `CSid` objeto.  
  
 `bSuccess`  
 Especifica si se deben auditar intentos de acceso permitido. Establezca esta marca en True para habilitar la auditoría; de lo contrario, establézcalo en false.  
  
 *bFailure*  
 Especifica si se deben auditar los intentos de acceso denegado. Establezca esta marca en True para habilitar la auditoría; de lo contrario, establézcalo en false.  
  
 `AceFlags`  
 Un conjunto de marcadores de bits que controlan la herencia de la ACE.  
  
 `pObjectType`  
 Tipo del objeto.  
  
 `pInheritedObjectType`  
 El tipo de objeto heredado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la ACE se agrega a la `CSacl` objeto, **false** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Un `CSacl` objeto contiene entradas de control de acceso (ACE) que especifican los tipos de intentos de acceso que generan registros de auditoría en el registro de eventos de seguridad. Este método agrega una entrada ACE para el `CSacl` objeto. La segunda forma de `AddAuditAce` solo está disponible en Windows 2000 y versiones posteriores.  
  
 Vea [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) para obtener una descripción de las diversas marcas que se puede establecer en el `AceFlags` parámetro.  
  
##  <a name="csacl"></a>CSacl::CSacl  
 El constructor.  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 Existente **ACL** estructura (lista de control de acceso).  
  
### <a name="remarks"></a>Comentarios  
 El `CSacl` objeto puede crearse de forma opcional con existente **ACL** estructura. Asegúrese de que este parámetro es una lista de control de acceso de sistema (SACL) y no una lista de control de acceso discrecional (DACL). En las compilaciones de depuración, si se proporciona una DACL se producirá una aserción. En versiones de lanzamiento se omiten todas las entradas de una DACL.  
  
##  <a name="dtor"></a>CSacl:: ~ CSacl  
 Destructor.  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera los recursos adquiridos por el objeto, incluidas todas las entradas de control de acceso (ACE).  
  
##  <a name="getacecount"></a>CSacl::GetAceCount  
 Devuelve el número de entradas de control de acceso (ACE) en el `CSacl` objeto.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de ACE contenidos en la `CSacl` objeto.  
  
##  <a name="operator_eq"></a>CSacl::operator =  
 Operador de asignación.  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El **ACL** (lista de control de acceso) para asignar al objeto existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la actualización `CSacl` objeto. Asegúrese de que el **ACL** parámetro es realmente una lista de control de acceso de sistema (SACL) y no una lista de control de acceso discrecional (DACL). En compilaciones de depuración, se producirá una aserción y en versiones de lanzamiento del **ACL** parámetro se omitirá.  
  
##  <a name="removeace"></a>CSacl::RemoveAce  
 Quita una ACE específica (entrada de control de acceso) de la **CSacl** objeto.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de la entrada ACE que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método se deriva de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>CSacl::RemoveAllAces  
 Quita todas las entradas de control de acceso (ACE) contenidas en el `CSacl` objeto.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita cada **ACE** estructura (si existe) en el `CSacl` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAcl](../../atl/reference/cacl-class.md)   
 [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)

