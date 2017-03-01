---
title: Clase CAcl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAcl
- ATL::CAcl
- ATLSECURITY/CAcl
- ATL.CAcl
dev_langs:
- C++
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
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
ms.openlocfilehash: 52de083664c2e9ca00a140450cb43372aff28428
ms.lasthandoff: 02/24/2017

---
# <a name="cacl-class"></a>Clase CAcl
Esta clase es un contenedor para un `ACL` estructura (lista de control de acceso).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAcl
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Una matriz de `ACCESS_MASK`s.|  
|[CAcl::CAceFlagArray](#caceflagarray)|Una matriz de `BYTE`s.|  
|[CAcl::CAceTypeArray](#cacetypearray)|Una matriz de `BYTE`s.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAcl::CAcl](#cacl)|El constructor.|  
|[CAcl:: ~ CAcl](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAcl::GetAceCount](#getacecount)|Devuelve al número de control de acceso a objetos de entrada (ACE).|  
|[CAcl::GetAclEntries](#getaclentries)|Recupera las entradas de control de acceso (ACL) de la lista de los `CAcl` objeto.|  
|[CAcl::GetAclEntry](#getaclentry)|Recupera toda la información sobre una entrada en un `CAcl` objeto.|  
|[CAcl::GetLength](#getlength)|Devuelve la longitud de la ACL.|  
|[CAcl::GetPACL](#getpacl)|Devuelve un paquetes (puntero a una ACL).|  
|[CAcl::IsEmpty](#isempty)|Pruebas del `CAcl` objeto para las entradas.|  
|[CAcl::IsNull](#isnull)|Devuelve el estado de la `CAcl` objeto.|  
|[CAcl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) de la `CAcl` objeto.|  
|[CAcl::RemoveAces](#removeaces)|Quita todas las entradas de control de acceso de la `CAcl` que se aplican a la determinada `CSid`.|  
|[CAcl::SetEmpty](#setempty)|Las marcas de la `CAcl` objeto como vacío.|  
|[CAcl::SetNull](#setnull)|Las marcas de la `CAcl` objeto como `NULL`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ACL de const CAcl::operator *](#operator_const_acl__star)|Conversiones de un `CAcl` objeto un `ACL` estructura.|  
|[CAcl::operator =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 El **ACL** estructura es el encabezado de una ACL (lista de control de acceso). Una ACL incluye una lista secuencial de cero o más [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868) (entradas de control de acceso). Las ACE individuales de una ACL se numeran de 0 a *n-1*, donde *n* es el número de ACE de la ACL. Al modificar una ACL, una aplicación hace referencia a una entrada de control de acceso (ACE) en la ACL por su índice.  
  
 Hay dos tipos ACL:  
  
-   Discrecional  
  
-   Sistema  
  
 Una ACL discrecional está controlada por el propietario de un objeto o cualquier persona concedido **WRITE_DAC** acceso al objeto. Especifica que el acceso a usuarios y grupos concretos pueden tener a un objeto. Por ejemplo, el propietario de un archivo puede utilizar una ACL discrecional para controlar qué usuarios y grupos pueden y no puede tener acceso al archivo.  
  
 Un objeto también puede tener información de seguridad de nivel de sistema asociado, en forma de un sistema controlado por un administrador del sistema ACL. Un ACL del sistema puede permitir que el administrador del sistema auditar los intentos de obtener acceso a un objeto.  
  
 Para obtener más detalles, consulte la [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872) discusión en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener una introducción al modelo de control de acceso de Windows, consulte [de Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="a-namecaccessmaskarraya--caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray  
 Una matriz de objetos ACCESS_MASK.  
  
```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta definición de tipo especifica el tipo de matriz que se puede utilizar para almacenar los derechos de acceso que se utiliza en las entradas de control de acceso (ACE).  
  
##  <a name="a-namecaceflagarraya--caclcaceflagarray"></a><a name="caceflagarray"></a>CAcl::CAceFlagArray  
 Una matriz de BYTEs.  
  
```
typedef CAtlArray<BYTE> CAceFlagArray;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta definición de tipo especifica el tipo de matriz que se utiliza para definir las marcas de control específicos del tipo de control de acceso (ACE) de entrada. Consulte la [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) definición de la lista completa de marcas posibles.  
  
##  <a name="a-namecacetypearraya--caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CAceTypeArray  
 Una matriz de BYTEs.  
  
```
typedef CAtlArray<BYTE> CAceTypeArray;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta definición de tipo especifica el tipo de matriz que se utiliza para definir la naturaleza de los objetos de control de acceso (ACE) de entrada, como ACCESS_ALLOWED_ACE_TYPE o ACCESS_DENIED_ACE_TYPE. Consulte la [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) definición de la lista completa de los tipos posibles.  
  
##  <a name="a-namecacla--caclcacl"></a><a name="cacl"></a>CAcl::CAcl  
 El constructor.  
  
```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 Objeto `CAcl` existente.  
  
### <a name="remarks"></a>Comentarios  
 El `CAcl` objeto puede crearse opcionalmente mediante existente `CAcl` objeto.  
  
##  <a name="a-namedtora--caclcacl"></a><a name="dtor"></a>CAcl:: ~ CAcl  
 Destructor.  
  
```
virtual ~CAcl() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera los recursos adquiridos por el objeto.  
  
##  <a name="a-namegetacecounta--caclgetacecount"></a><a name="getacecount"></a>CAcl::GetAceCount  
 Devuelve al número de control de acceso a objetos de entrada (ACE).  
  
```
virtual UINT GetAceCount() const throw() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de entradas ACE en la `CAcl` objeto.  
  
##  <a name="a-namegetaclentriesa--caclgetaclentries"></a><a name="getaclentries"></a>CAcl::GetAclEntries  
 Recupera las entradas de control de acceso (ACL) de la lista de los `CAcl` objeto.  
  
```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSids`  
 Un puntero a una matriz de [CSid](../../atl/reference/csid-class.md) objetos.  
  
 *pAccessMasks*  
 Las máscaras de acceso.  
  
 *pAceTypes*  
 La entrada de control de acceso ( **ACE**) tipos.  
  
 *pAceFlags*  
 El **ACE** marcas.  
  
### <a name="remarks"></a>Comentarios  
 Este método rellena los parámetros de matriz con los detalles de cada **ACE** objeto contenido en el `CAcl` objeto. Utilice NULL cuando no se requieren los detalles de esa matriz determinado.  
  
 El contenido de cada matriz corresponde entre sí, es decir, el primer elemento de la `CAccessMaskArray` matriz corresponde al primer elemento en el `CSidArray` matriz y así sucesivamente.  
  
 Consulte [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) para obtener más detalles sobre los tipos ACE y marcas.  
  
##  <a name="a-namegetaclentrya--caclgetaclentry"></a><a name="getaclentry"></a>CAcl::GetAclEntry  
 Recupera toda la información sobre una entrada en una lista de control de acceso (ACL).  
  
```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de la entrada ACL a recuperar.  
  
 `pSid`  
 El [CSid](../../atl/reference/csid-class.md) del objeto al que se aplica la entrada de ACL.  
  
 *pMask*  
 La máscara de especificación de permisos para conceder o denegar el acceso.  
  
 `pType`  
 El tipo de ACE.  
  
 `pFlags`  
 Los indicadores ACE.  
  
 `pObjectType`  
 Tipo del objeto. Esto establecerá en GUID_NULL si no se especifica el tipo de objeto en la ACE, o si no, la ACE es una ACE del objeto.  
  
 `pInheritedObjectType`  
 El tipo de objeto heredado. Esto establecerá en GUID_NULL si no se especifica el tipo de objeto heredado de la ACE, o si no, la ACE es una ACE del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera toda la información sobre una ACE individual, que proporciona más información que [CAcl::GetAclEntries](#getaclentries) sólo hace que estén disponibles.  
  
 Consulte [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) para obtener más detalles sobre los tipos ACE y marcas.  
  
##  <a name="a-namegetlengtha--caclgetlength"></a><a name="getlength"></a>CAcl::GetLength  
 Devuelve la longitud de la lista de control de acceso (ACL).  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud requerida en bytes necesarios para contener el **ACL** estructura.  
  
##  <a name="a-namegetpacla--caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL  
 Devuelve un puntero a una lista de control de acceso (ACL).  
  
```
const ACL* GetPACL() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la **ACL** estructura.  
  
##  <a name="a-nameisemptya--caclisempty"></a><a name="isempty"></a>CAcl::IsEmpty  
 Pruebas del `CAcl` objeto para las entradas.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** si la `CAcl` objeto no es NULL y no contiene ninguna entrada. Devuelve **false** si la `CAcl` objeto es NULL o contiene al menos una entrada.  
  
##  <a name="a-nameisnulla--caclisnull"></a><a name="isnull"></a>CAcl::IsNull  
 Devuelve el estado de la `CAcl` objeto.  
  
```
bool IsNull() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la `CAcl` objeto es NULL, **false** en caso contrario.  
  
##  <a name="a-nameoperatorconstaclstara--cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>ACL de const CAcl::operator *  
 Conversiones de un `CAcl` objeto un **ACL** estructura (lista de control de acceso).  
  
```  
operator const ACL *() const throw(...);
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la dirección de la **ACL** estructura.  
  
##  <a name="a-nameoperatoreqa--cacloperator-"></a><a name="operator_eq"></a>CAcl::operator =  
 Operador de asignación.  
  
```
CAcl& operator= (const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El `CAcl` para asignar al objeto existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la actualización `CAcl` objeto.  
  
##  <a name="a-nameremoveacea--caclremoveace"></a><a name="removeace"></a>CAcl::RemoveAce  
 Quita una ACE específica (entrada de control de acceso) de la **CAcl** objeto.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de la entrada ACE que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método se deriva [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="a-nameremoveacesa--caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces  
 Quita todos las ACE (entradas de control de acceso) de la `CAcl` que se aplican a la determinada `CSid`.  
  
```
bool RemoveAces(const CSid& rSid) throw(...)
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 Referencia a un objeto `CSid`.  
  
##  <a name="a-namesetemptya--caclsetempty"></a><a name="setempty"></a>CAcl::SetEmpty  
 Las marcas de la `CAcl` objeto como vacío.  
  
```
void SetEmpty() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El `CAcl` se puede establecer está vacío o es NULL: los dos estados son diferentes.  
  
##  <a name="a-namesetnulla--caclsetnull"></a><a name="setnull"></a>CAcl::SetNull  
 Las marcas de la `CAcl` objeto como NULL.  
  
```
void SetNull() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El `CAcl` se puede establecer está vacío o es NULL: los dos estados son diferentes.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)

