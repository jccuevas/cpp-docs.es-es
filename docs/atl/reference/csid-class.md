---
title: Clase de CSid | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
dev_langs:
- C++
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
caps.latest.revision: 24
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
ms.openlocfilehash: ceb0ab95d18e1336584eab45bc00ce769efd7384
ms.lasthandoff: 02/24/2017

---
# <a name="csid-class"></a>CSid (clase)
Esta clase es un contenedor para un `SID` estructura (identificador de seguridad).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CSid
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSid::CSidArray](#csidarray)|Matriz de objetos `CSid`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSid::CSid](#csid)|El constructor.|  
|[CSid:: ~ CSid](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSid::AccountName](#accountname)|Devuelve el nombre de la cuenta asociada con el `CSid` objeto.|  
|[CSid::Domain](#domain)|Devuelve el nombre de dominio asociado a la `CSid` objeto.|  
|[CSid::EqualPrefix](#equalprefix)|Pruebas `SID` prefijos (identificador de seguridad) son iguales.|  
|[CSid::GetLength](#getlength)|Devuelve la longitud de la `CSid` objeto.|  
|[CSid::GetPSID](#getpsid)|Devuelve un puntero a un `SID` estructura.|  
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Devuelve un puntero a la **SID_IDENTIFIER_AUTHORITY** estructura.|  
|[CSid::GetSubAuthority](#getsubauthority)|Devuelve un subautoridad especificado en un **SID** estructura.|  
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Devuelve el recuento de subautoridad.|  
|[CSid::IsValid](#isvalid)|Pruebas del `CSid` objeto válido.|  
|[CSid::LoadAccount](#loadaccount)|Las actualizaciones de la `CSid` objeto, dado el nombre de cuenta y dominio o una existente `SID` estructura.|  
|[CSid::Sid](#sid)|Devuelve la cadena de identificador.|  
|[CSid::SidNameUse](#sidnameuse)|Devuelve una descripción del estado de la `CSid` objeto.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](#operator_eq)|Operador de asignación.|  
|[operador SID const *](#operator_const_sid__star)|Conversiones de un `CSid` objeto a un puntero a un `SID` estructura.|  
  
### <a name="global-operators"></a>Operadores globales  
  
|||  
|-|-|  
|[operador ==](#operator_eq_eq)|Comprueba la igualdad de dos objetos de descriptor de seguridad|  
|[operador! =](#operator_neq)|Comprueba dos objetos de descriptor de seguridad no son iguales|  
|[(operador)\<](#operator_lt_)|Compara el valor relativo de dos objetos de descriptor de seguridad.|  
|[operador >](#operator_gt_)|Compara el valor relativo de dos objetos de descriptor de seguridad.|  
|[(operador)\<=](#operator_lt__eq)|Compara el valor relativo de dos objetos de descriptor de seguridad.|  
|[operador > =](#operator_gt__eq)|Compara el valor relativo de dos objetos de descriptor de seguridad.|  
  
## <a name="remarks"></a>Comentarios  
 El `SID` estructura es una estructura de longitud variable que se utiliza para identificar usuarios o grupos.  
  
 Las aplicaciones no deben modificar el `SID` estructura directamente, sino usar los métodos proporcionados en esta clase contenedora. Consulte también [AtlGetOwnerSid](http://msdn.microsoft.com/library/0e3a2606-74b8-4412-9803-bb437e22da85), [AtlSetGroupSid](http://msdn.microsoft.com/library/83531d32-11ab-4a68-a3c6-1bfa54ab8dfa), [AtlGetGroupSid](http://msdn.microsoft.com/library/8e7ec6b9-15c8-4a8a-977e-1e4c853d0be7), y [AtlSetOwnerSid](http://msdn.microsoft.com/library/3a8abb76-1d2c-465d-a5e8-62a12a3c37f3).  
  
 Para obtener una introducción al modelo de control de acceso de Windows, consulte [de Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="accountname"></a>CSid::AccountName  
 Devuelve el nombre de la cuenta asociada con el `CSid` objeto.  
  
```
LPCTSTR AccountName() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el `LPCTSTR` seleccionando el nombre de la cuenta.  
  
### <a name="remarks"></a>Comentarios  
 Este método intenta encontrar un nombre especificado `SID` (identificador de seguridad). Para obtener más información, consulte [LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166).  
  
 Si ningún nombre de cuenta para la `SID` se puede encontrar, `AccountName` devuelve una cadena vacía. Esto puede ocurrir si hay un tiempo de espera de la red impide que buscar el nombre de este método. También se produce para los identificadores de seguridad con ningún nombre de cuenta correspondiente, como un inicio de sesión `SID` que identifica una sesión de inicio de sesión.  
  
##  <a name="csid"></a>CSid::CSid  
 El constructor.  
  
```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 Existente `CSid` objeto o `SID` estructura (identificador de seguridad).  
  
 *IdentifierAuthority*  
 La autoridad.  
  
 *nSubAuthorityCount*  
 El recuento de subautoridad.  
  
 `pszAccountName`  
 El nombre de cuenta.  
  
 `pszSystem`  
 El nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se utiliza en su lugar el sistema local.  
  
 `pSid`  
 Un puntero a un `SID` estructura.  
  
### <a name="remarks"></a>Comentarios  
 El constructor inicializa la `CSid` objeto, establecer un miembro de datos internos en *SidTypeInvalid*, o copiando la configuración a partir de una `CSid`, `SID`, o la cuenta existente.  
  
 Si se produce un error en la inicialización, el constructor producirá una [CAtlException clase](../../atl/reference/catlexception-class.md).  
  
##  <a name="dtor"></a>CSid:: ~ CSid  
 Destructor.  
  
```
virtual ~CSid() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera los recursos adquiridos por el objeto.  
  
##  <a name="csidarray"></a>CSid::CSidArray  
 Una matriz de [CSid](../../atl/reference/csid-class.md) objetos.  
  
```
typedef CAtlArray<CSid> CSidArray;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta definición de tipo especifica el tipo de matriz que se puede utilizar para recuperar los identificadores de seguridad de una ACL (lista de control de acceso). Consulte [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).  
  
##  <a name="domain"></a>CSid::Domain  
 Devuelve el nombre de dominio asociado a la `CSid` objeto.  
  
```
LPCTSTR Domain() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el `LPCTSTR` que apunta al dominio.  
  
### <a name="remarks"></a>Comentarios  
 Este método intenta encontrar un nombre especificado `SID` (identificador de seguridad). Para obtener más información, consulte [LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166).  
  
 Si ningún nombre de cuenta para la `SID` se puede encontrar, **dominio** devuelve el dominio como una cadena vacía. Esto puede ocurrir si hay un tiempo de espera de la red impide que buscar el nombre de este método. También se produce para los identificadores de seguridad con ningún nombre de cuenta correspondiente, como un inicio de sesión `SID` que identifica una sesión de inicio de sesión.  
  
##  <a name="equalprefix"></a>CSid::EqualPrefix  
 Pruebas `SID` prefijos (identificador de seguridad) son iguales.  
  
```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El `SID` estructura (identificador de seguridad) o `CSid` objeto que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** correctamente, **false** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [EqualPrefixSid](http://msdn.microsoft.com/library/windows/desktop/aa446621) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más detalles.  
  
##  <a name="getlength"></a>CSid::GetLength  
 Devuelve la longitud de la `CSid` objeto.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud en bytes de la `CSid` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el `CSid` estructura no es válida, el valor devuelto es indefinido. Antes de llamar a `GetLength`, utilice el [CSid::IsValid](#isvalid) función miembro para comprobar que `CSid` es válida.  
  
> [!NOTE]
>  En compilaciones de depuración, la función producirá una aserción si el `CSid` objeto no es válido.  
  
##  <a name="getpsid"></a>CSid::GetPSID  
 Devuelve un puntero a un `SID` estructura (identificador de seguridad).  
  
```
const SID* GetPSID() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la dirección de la `CSid` objeto subyacente del `SID` estructura.  
  
##  <a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY  
 Devuelve un puntero a la **SID_IDENTIFIER_AUTHORITY** estructura.  
  
```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve la dirección de la **SID_IDENTIFIER_AUTHORITY** estructura. Si se produce un error, el valor devuelto es indefinido. Error puede producirse si la `CSid` objeto no es válido, en cuyo caso el [CSid::IsValid](#isvalid) método devuelve **false**. La función `GetLastError` se puede llamar para obtener información de error extendido.  
  
> [!NOTE]
>  En compilaciones de depuración, la función producirá una aserción si el `CSid` objeto no es válido.  
  
##  <a name="getsubauthority"></a>CSid::GetSubAuthority  
 Devuelve un subautoridad especificado en un `SID` estructura (identificador de seguridad).  
  
```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nSubAuthority*  
 Subautoridad.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la subautoridad hace referencia a *nSubAuthority.* El valor de subautoridad es un identificador relativo (RID).  
  
### <a name="remarks"></a>Comentarios  
 El *nSubAuthority* parámetro especifica un valor de índice que identifica el elemento de matriz de subautoridad devolverá el método. El método realiza ninguna prueba de validación en este valor. Una aplicación puede llamar a [CSid::GetSubAuthorityCount](#getsubauthoritycount) para detectar el intervalo de valores aceptables.  
  
> [!NOTE]
>  En compilaciones de depuración, la función producirá una aserción si el `CSid` objeto no es válido.  
  
##  <a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount  
 Devuelve el recuento de subautoridad.  
  
```
UCHAR GetSubAuthorityCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es el recuento de subautoridad.  
  
 Si se produce un error en el método, el valor devuelto es indefinido. El método produce un error si la `CSid` objeto no es válido. Para obtener información de errores extendida, realice una llamada a `GetLastError`.  
  
> [!NOTE]
>  En compilaciones de depuración, la función producirá una aserción si el `CSid` objeto no es válido.  
  
##  <a name="isvalid"></a>CSid::IsValid  
 Pruebas del `CSid` objeto válido.  
  
```
bool IsValid() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la `CSid` objeto es válido, **false** si no es así. No hay ninguna información de error extendida para este método; No llame a `GetLastError`.  
  
### <a name="remarks"></a>Comentarios  
 El `IsValid` método valida la `CSid` objeto comprobando que el número de revisión está dentro de un intervalo conocido y que el número de campos subauthorities es menor que el máximo.  
  
##  <a name="loadaccount"></a>CSid::LoadAccount  
 Las actualizaciones de la `CSid` objeto, dado el nombre de cuenta y el dominio o una estructura de SID (identificador de seguridad).  
  
```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszAccountName`  
 El nombre de cuenta.  
  
 `pszSystem`  
 El nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se utiliza en su lugar el sistema local.  
  
 `pSid`  
 Un puntero a un [SID](http://msdn.microsoft.com/library/windows/desktop/aa379594\(v=vs.85\).aspx) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** correctamente, **false** en caso de error. Para obtener información de errores extendida, realice una llamada a `GetLastError`.  
  
### <a name="remarks"></a>Comentarios  
 `LoadAccount`intenta encontrar un identificador de seguridad para el nombre especificado. Consulte [LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166\(v=vs.85\).aspx) para obtener más detalles.  
  
##  <a name="operator_eq"></a>CSid::operator =  
 Operador de asignación.  
  
```
CSid& operator= (const CSid& rhs) throw(...);  
CSid& operator= (const SID& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 El `SID` (identificador de seguridad) o `CSid` para asignar a la `CSid` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la actualización `CSid` objeto.  
  
##  <a name="operator_eq_eq"></a>CSid::operator ==  
 Comprueba la igualdad de dos objetos de descriptor de seguridad.  
  
```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador ==.  
  
 `rhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho del operador ==.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los descriptores de seguridad son iguales; en caso contrario **false**.  
  
##  <a name="operator_neq"></a>CSid::operator! =  
 Comprueba dos objetos de descriptor de seguridad no son iguales.  
  
```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).  
  
 `rhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los descriptores de seguridad no son iguales; en caso contrario **false**.  
  
##  <a name="operator_lt"></a>CSid::operator&lt;  
 Compara el valor relativo de dos objetos de descriptor de seguridad.  
  
```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).  
  
 `rhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si `lhs` es menor que `rhs`, de lo contrario, **false**.  
  
##  <a name="operator_lt__eq"></a>CSid::operator&lt;=  
 Compara el valor relativo de dos objetos de descriptor de seguridad.  
  
```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).  
  
 `rhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si `lhs` es menor o igual a `rhs`, de lo contrario, **false**.  
  
##  <a name="operator_gt"></a>CSid::operator&gt;  
 Compara el valor relativo de dos objetos de descriptor de seguridad.  
  
```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).  
  
 `rhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si `lhs` es mayor que `rhs`, de lo contrario, **false**.  
  
##  <a name="operator_gt__eq"></a>CSid::operator&gt;=  
 Compara el valor relativo de dos objetos de descriptor de seguridad.  
  
```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).  
  
 `rhs`  
 El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si `lhs` es mayor o igual a `rhs`, de lo contrario, **false**.  
  
##  <a name="operator_const_sid__star"></a>SID de const CSid::operator *  
 Conversiones de un `CSid` objeto a un puntero a un `SID` estructura (identificador de seguridad).  
  
```  
operator const SID *() const throw(...);
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la dirección de la `SID` estructura.  
  
##  <a name="sid"></a>CSid::Sid  
 Devuelve el `SID` (estructura) (identificador de seguridad) como una cadena.  
  
```
LPCTSTR Sid() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el `SID` estructura como una cadena en un formato adecuado para mostrar, el almacenamiento o la transmisión. Equivalente a [ConvertSidToStringSid](http://msdn.microsoft.com/library/windows/desktop/aa376399), aunque esta función sólo está disponible en Windows 2000 o posterior y por lo que se emula para sistemas operativos anteriores.  
  
##  <a name="sidnameuse"></a>CSid::SidNameUse  
 Devuelve una descripción del estado de la `CSid` objeto.  
  
```
SID_NAME_USE SidNameUse() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del miembro de datos que almacena un valor que describe el estado de la `CSid` objeto.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SidTypeUser|Indica un usuario `SID` (identificador de seguridad).|  
|SidTypeGroup|Indica un grupo de `SID`.|  
|SidTypeDomain|Indica un dominio `SID`.|  
|SidTypeAlias|Indica un alias `SID`.|  
|SidTypeWellKnownGroup|Indica un `SID` para un grupo conocido.|  
|SidTypeDeletedAccount|Indica un `SID` de una cuenta eliminada.|  
|SidTypeInvalid|Indica un válido `SID`.|  
|SidTypeUnknown|Indica un estado desconocido `SID` tipo.|  
|SidTypeComputer|Indica un `SID` para un equipo.|  
  
### <a name="remarks"></a>Comentarios  
 Llame a [CSid::LoadAccount](#loadaccount) actualizar el `CSid` objeto antes de llamar a `SidNameUse` para devolver su estado. `SidNameUse`no cambia el estado del objeto (mediante una llamada a **LookupAccountName** o **LookupAccountSid**), pero sólo se devuelve el estado actual.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de seguridad](../../visual-cpp-samples.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)   
 [Operadores](../../atl/reference/atl-operators.md)

