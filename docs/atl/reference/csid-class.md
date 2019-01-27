---
title: CSid (clase)
ms.date: 11/04/2016
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
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: 6fcff646a577500fd05b7c938b2c336ebe725957
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894320"
---
# <a name="csid-class"></a>CSid (clase)

Esta clase es un contenedor para un `SID` estructura (identificador de seguridad).

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSid
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Matriz de objetos `CSid`.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSid::CSid](#csid)|El constructor.|
|[CSid::~CSid](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Devuelve el nombre de la cuenta asociada con el `CSid` objeto.|
|[CSid::Domain](#domain)|Devuelve el nombre de dominio asociado a la `CSid` objeto.|
|[CSid::EqualPrefix](#equalprefix)|Pruebas `SID` prefijos (identificador de seguridad) para la igualdad.|
|[CSid::GetLength](#getlength)|Devuelve la longitud de la `CSid` objeto.|
|[CSid::GetPSID](#getpsid)|Devuelve un puntero a un `SID` estructura.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Devuelve un puntero a la `SID_IDENTIFIER_AUTHORITY` estructura.|
|[CSid::GetSubAuthority](#getsubauthority)|Devuelve un subautoridad especificado en un `SID` estructura.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Devuelve el recuento de subauthority.|
|[CSid::IsValid](#isvalid)|Las pruebas del `CSid` objeto cuya validez.|
|[CSid::LoadAccount](#loadaccount)|Las actualizaciones de la `CSid` objeto según el nombre de cuenta y dominio o una existente `SID` estructura.|
|[CSid::Sid](#sid)|Devuelve la cadena de identificador.|
|[CSid::SidNameUse](#sidnameuse)|Devuelve una descripción del estado de la `CSid` objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator =](#operator_eq)|Operador de asignación.|
|[SID de operador const *](#operator_const_sid__star)|Convierte un `CSid` objeto a un puntero a un `SID` estructura.|

### <a name="global-operators"></a>Operadores globales

|||
|-|-|
|[operator ==](#operator_eq_eq)|Comprueba dos objetos de descriptor de seguridad para la igualdad|
|[operator !=](#operator_neq)|Comprueba dos objetos de descriptor de seguridad no son iguales|
|[Operador \<](#operator_lt_)|Compara el valor relativo de dos objetos de descriptor de seguridad.|
|[operator >](#operator_gt_)|Compara el valor relativo de dos objetos de descriptor de seguridad.|
|[Operador \<=](#operator_lt__eq)|Compara el valor relativo de dos objetos de descriptor de seguridad.|
|[operator >=](#operator_gt__eq)|Compara el valor relativo de dos objetos de descriptor de seguridad.|

## <a name="remarks"></a>Comentarios

El `SID` estructura es una estructura de longitud variable que se utiliza para identificar usuarios o grupos.

Las aplicaciones no deben modificar el `SID` estructura directamente, pero en su lugar, use los métodos proporcionados en esta clase contenedora. Vea también [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid), y [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="accountname"></a>  CSid::AccountName

Devuelve el nombre de la cuenta asociada con el `CSid` objeto.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve el LPCTSTR seleccionando el nombre de la cuenta.

### <a name="remarks"></a>Comentarios

Este método intenta encontrar un nombre para el elemento especificado `SID` (identificador de seguridad). Para obtener más información, consulte [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Si ningún nombre de cuenta para el `SID` puede encontrarse, `AccountName` devuelve una cadena vacía. Esto puede ocurrir si un tiempo de espera de la red impide que buscar el nombre de este método. También se produce para los identificadores de seguridad con ningún nombre de cuenta correspondiente, como un inicio de sesión `SID` que identifica una sesión de inicio de sesión.

##  <a name="csid"></a>  CSid::CSid

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

*rhs*<br/>
Existente `CSid` objeto o `SID` estructura (identificador de seguridad).

*IdentifierAuthority*<br/>
La entidad.

*nSubAuthorityCount*<br/>
El recuento de subauthority.

*pszAccountName*<br/>
El nombre de cuenta.

*pszSystem*<br/>
El nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se usa en su lugar, el sistema local.

*pSid*<br/>
Un puntero a un `SID` estructura.

### <a name="remarks"></a>Comentarios

El constructor inicializa el `CSid` objeto, si se establece en un miembro de datos interno *SidTypeInvalid*, o copiando la configuración a partir de una máquina `CSid`, `SID`, o una cuenta existente.

Si se produce un error de inicialización, el constructor produce una [CAtlException (clase)](../../atl/reference/catlexception-class.md).

##  <a name="dtor"></a>  CSid::~CSid

Destructor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera los recursos adquiridos por el objeto.

##  <a name="csidarray"></a>  CSid::CSidArray

Una matriz de [CSid](../../atl/reference/csid-class.md) objetos.

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Comentarios

Esta definición de tipo especifica el tipo de matriz que puede usarse para recuperar los identificadores de seguridad de una ACL (lista de control de acceso). Consulte [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

##  <a name="domain"></a>  CSid::Domain

Devuelve el nombre de dominio asociado a la `CSid` objeto.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve el `LPCTSTR` que apunta al dominio.

### <a name="remarks"></a>Comentarios

Este método intenta encontrar un nombre para el elemento especificado `SID` (identificador de seguridad). Para obtener más información, consulte [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Si ningún nombre de cuenta para el `SID` puede encontrarse, `Domain` devuelve el dominio como una cadena vacía. Esto puede ocurrir si un tiempo de espera de la red impide que buscar el nombre de este método. También se produce para los identificadores de seguridad con ningún nombre de cuenta correspondiente, como un inicio de sesión `SID` que identifica una sesión de inicio de sesión.

##  <a name="equalprefix"></a>  CSid::EqualPrefix

Pruebas `SID` prefijos (identificador de seguridad) para la igualdad.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
El `SID` estructura (identificador de seguridad) o `CSid` objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Consulte [EqualPrefixSid](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) en el SDK de Windows para obtener más detalles.

##  <a name="getlength"></a>  CSid::GetLength

Devuelve la longitud de la `CSid` objeto.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud en bytes de la `CSid` objeto.

### <a name="remarks"></a>Comentarios

Si el `CSid` estructura no es válida, el valor devuelto es indefinido. Antes de llamar a `GetLength`, utilice el [CSid::IsValid](#isvalid) función miembro para comprobar que `CSid` es válido.

> [!NOTE]
>  En las compilaciones de depuración para la función provocará una aserción si el `CSid` objeto no es válido.

##  <a name="getpsid"></a>  CSid::GetPSID

Devuelve un puntero a un `SID` estructura (identificador de seguridad).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección de la `CSid` objeto subyacente del `SID` estructura.

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

Devuelve un puntero a la `SID_IDENTIFIER_AUTHORITY` estructura.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve la dirección de la `SID_IDENTIFIER_AUTHORITY` estructura. Si se produce un error, el valor devuelto es indefinido. Puede producirse un error si el `CSid` objeto no es válido, en cuyo caso el [CSid::IsValid](#isvalid) método devuelve FALSE. La función `GetLastError` se puede llamar para obtener información de error extendido.

> [!NOTE]
>  En las compilaciones de depuración para la función provocará una aserción si el `CSid` objeto no es válido.

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

Devuelve un subautoridad especificado en un `SID` estructura (identificador de seguridad).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parámetros

*nSubAuthority*<br/>
La subautoridad.

### <a name="return-value"></a>Valor devuelto

Devuelve la subautoridad al que hace referencia *nSubAuthority.* El valor de subautoridad es un identificador relativo (RID).

### <a name="remarks"></a>Comentarios

El *nSubAuthority* parámetro especifica un valor de índice que identifica el elemento de matriz subautoridad devolverá el método. El método realiza ninguna prueba de validación en este valor. Una aplicación puede llamar a [CSid::GetSubAuthorityCount](#getsubauthoritycount) para detectar el intervalo de valores aceptables.

> [!NOTE]
>  En las compilaciones de depuración para la función provocará una aserción si el `CSid` objeto no es válido.

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

Devuelve el recuento de subauthority.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método tiene éxito, el valor devuelto es el recuento de subauthority.

Si se produce un error en el método, el valor devuelto es indefinido. El método produce un error si el `CSid` objeto no es válido. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

> [!NOTE]
>  En las compilaciones de depuración para la función provocará una aserción si el `CSid` objeto no es válido.

##  <a name="isvalid"></a>  CSid::IsValid

Las pruebas del `CSid` objeto cuya validez.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el `CSid` objeto es válido, FALSE si no lo es. No hay ninguna información de error extendida para este método; No llame a `GetLastError`.

### <a name="remarks"></a>Comentarios

El `IsValid` método valida la `CSid` objeto comprobando que el número de revisión está dentro del intervalo conocido y que el número de campos subauthorities es menor que el máximo.

##  <a name="loadaccount"></a>  CSid::LoadAccount

Las actualizaciones de la `CSid` objeto según el nombre de cuenta y dominio o una estructura de SID (identificador de seguridad) existente.

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszAccountName*<br/>
El nombre de cuenta.

*pszSystem*<br/>
El nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se usa en su lugar, el sistema local.

*pSid*<br/>
Un puntero a un [SID](/windows/desktop/api/winnt/ns-winnt-_sid) estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Comentarios

`LoadAccount` intenta encontrar un identificador de seguridad para el nombre especificado. Consulte [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida) para obtener más detalles.

##  <a name="operator_eq"></a>  CSid::operator =

Operador de asignación.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
El `SID` (identificador de seguridad) o `CSid` para asignar a la `CSid` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la actualización `CSid` objeto.

##  <a name="operator_eq_eq"></a>  CSid::operator ==

Comprueba dos objetos de descriptor de seguridad para la igualdad.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador ==.

*rhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho del operador ==.

### <a name="return-value"></a>Valor devuelto

TRUE si los descriptores de seguridad son iguales, de lo contrario, FALSE.

##  <a name="operator_neq"></a>  CSid::operator !=

Comprueba dos objetos de descriptor de seguridad no son iguales.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).

*rhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).

### <a name="return-value"></a>Valor devuelto

TRUE si los descriptores de seguridad no son iguales, de lo contrario, FALSE.

##  <a name="operator_lt"></a>  CSid::operator &lt;

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).

*rhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).

### <a name="return-value"></a>Valor devuelto

TRUE si *lhs* es menor que *rhs*, de lo contrario, FALSE.

##  <a name="operator_lt__eq"></a>  CSid::operator &lt;=

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).

*rhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).

### <a name="return-value"></a>Valor devuelto

TRUE si *lhs* es menor o igual que *rhs*, de lo contrario, FALSE.

##  <a name="operator_gt"></a>  CSid::operator &gt;

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).

*rhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).

### <a name="return-value"></a>Valor devuelto

TRUE si *lhs* es mayor que *rhs*, de lo contrario, FALSE.

##  <a name="operator_gt__eq"></a>  CSid::operator &gt;=

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado izquierdo de la! = (operador).

*rhs*<br/>
El `SID` (identificador de seguridad) o `CSid` que aparece en el lado derecho de la! = (operador).

### <a name="return-value"></a>Valor devuelto

TRUE si *lhs* es mayor o igual a *rhs*, de lo contrario, FALSE.

##  <a name="operator_const_sid__star"></a>  SID const CSid::operator \*

Convierte un `CSid` objeto a un puntero a un `SID` estructura (identificador de seguridad).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Devuelve la dirección de la `SID` estructura.

##  <a name="sid"></a>  CSid::Sid

Devuelve el `SID` estructura (identificador de seguridad) como una cadena.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve el `SID` estructura como una cadena en un formato adecuado para mostrar, almacenamiento o transmisión. Equivalente a [ConvertSidToStringSid](/windows/desktop/api/sddl/nf-sddl-convertsidtostringsida).

##  <a name="sidnameuse"></a>  CSid::SidNameUse

Devuelve una descripción del estado de la `CSid` objeto.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del miembro de datos que almacena un valor que describe el estado de la `CSid` objeto.

|Valor|Descripción|
|-----------|-----------------|
|SidTypeUser|Indica que un usuario `SID` (identificador de seguridad).|
|SidTypeGroup|Indica un grupo `SID`.|
|SidTypeDomain|Indica un dominio `SID`.|
|SidTypeAlias|Indica un alias `SID`.|
|SidTypeWellKnownGroup|Indica un `SID` para un grupo conocido.|
|SidTypeDeletedAccount|Indica un `SID` para una cuenta eliminada.|
|SidTypeInvalid|Indica un no válido `SID`.|
|SidTypeUnknown|Indica un estado desconocido `SID` tipo.|
|SidTypeComputer|Indica un `SID` para un equipo.|

### <a name="remarks"></a>Comentarios

Llame a [CSid::LoadAccount](#loadaccount) para actualizar el `CSid` objeto antes de llamar a `SidNameUse` para devolver su estado. `SidNameUse` no cambia el estado del objeto (mediante una llamada a `LookupAccountName` o `LookupAccountSid`), pero solo devuelve el estado actual.

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)<br/>
[Operadores](../../atl/reference/atl-operators.md)
