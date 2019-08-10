---
title: CSid (clase)
ms.date: 03/27/2019
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
ms.openlocfilehash: fb496e3bd58d0fe134c37b240eb2698302c6aa64
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915698"
---
# <a name="csid-class"></a>CSid (clase)

Esta clase es un contenedor para una `SID` estructura (identificador de seguridad).

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSid
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Matriz de objetos `CSid`.|

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSid::CSid](#csid)|El constructor.|
|[CSid::~CSid](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Devuelve el nombre de la cuenta asociada `CSid` al objeto.|
|[CSid::Domain](#domain)|Devuelve el nombre del dominio asociado `CSid` al objeto.|
|[CSid::EqualPrefix](#equalprefix)|Prefijos de pruebas `SID` (identificador de seguridad) para la igualdad.|
|[CSid::GetLength](#getlength)|Devuelve la longitud del `CSid` objeto.|
|[CSid::GetPSID](#getpsid)|Devuelve un puntero a una `SID` estructura.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Devuelve un puntero a la `SID_IDENTIFIER_AUTHORITY` estructura.|
|[CSid::GetSubAuthority](#getsubauthority)|Devuelve un subautor especificado en una `SID` estructura.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Devuelve el recuento de subautoridad.|
|[CSid::IsValid](#isvalid)|Comprueba la `CSid` validez del objeto.|
|[CSid::LoadAccount](#loadaccount)|Actualiza el `CSid` objeto dado el nombre de cuenta y el dominio, o `SID` una estructura existente.|
|[CSid::Sid](#sid)|Devuelve la cadena de identificador.|
|[CSid::SidNameUse](#sidnameuse)|Devuelve una descripción del estado del `CSid` objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#operator_eq)|Operador de asignación.|
|[Operator const SID *](#operator_const_sid__star)|Convierte un `CSid` objeto en un puntero a una `SID` estructura.|

### <a name="global-operators"></a>Operadores globales

|||
|-|-|
|[operator ==](#operator_eq_eq)|Comprueba la igualdad de dos objetos de descriptor de seguridad|
|[operator !=](#operator_neq)|Comprueba si dos objetos de descriptor de seguridad no son iguales|
|[Operator\<](#operator_lt)|Compara el valor relativo de dos objetos de descriptor de seguridad.|
|[operador >](#operator_gt)|Compara el valor relativo de dos objetos de descriptor de seguridad.|
|[Operator\<=](#operator_lt__eq)|Compara el valor relativo de dos objetos de descriptor de seguridad.|
|[operador > =](#operator_gt__eq)|Compara el valor relativo de dos objetos de descriptor de seguridad.|

## <a name="remarks"></a>Comentarios

La `SID` estructura es una estructura de longitud variable que se usa para identificar de forma única a los usuarios o grupos.

Las aplicaciones no deben modificar `SID` directamente la estructura, sino que usan los métodos proporcionados en esta clase contenedora. Vea también [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)y [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/desktop/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="accountname"></a>  CSid::AccountName

Devuelve el nombre de la cuenta asociada `CSid` al objeto.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve el LPCTSTR que apunta al nombre de la cuenta.

### <a name="remarks"></a>Comentarios

Este método intenta encontrar un nombre para el (identificador `SID` de seguridad) especificado. Para obtener información completa, vea [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Si no se `SID` puede encontrar ningún nombre de cuenta para `AccountName` , devuelve una cadena vacía. Esto puede ocurrir si un tiempo de espera de red impide que este método encuentre el nombre. También se produce para los identificadores de seguridad que no tienen el nombre de cuenta `SID` correspondiente, como un que identifica una sesión de inicio de sesión.

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
Una estructura `CSid` de objeto `SID` o de (identificador de seguridad) existente.

*IdentifierAuthority*<br/>
Autoridad.

*nSubAuthorityCount*<br/>
Recuento de subautoridad.

*pszAccountName*<br/>
El nombre de la cuenta.

*pszSystem*<br/>
Nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se utiliza en su lugar el sistema local.

*pSid*<br/>
Puntero a una `SID` estructura.

### <a name="remarks"></a>Comentarios

`CSid` El constructor inicializa el objeto, estableciendo un miembro de datos interno en *SidTypeInvalid*o copiando los `CSid`valores de una cuenta existente, `SID`o existente.

Si se produce un error de inicialización, el constructor producirá una [clase CAtlException](../../atl/reference/catlexception-class.md).

##  <a name="dtor"></a>  CSid::~CSid

Destructor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos adquiridos por el objeto.

##  <a name="csidarray"></a>  CSid::CSidArray

Una matriz de objetos [CSid](../../atl/reference/csid-class.md) .

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Comentarios

Este typedef especifica el tipo de matriz que se puede utilizar para recuperar los identificadores de seguridad de una ACL (lista de control de acceso). Vea [CAcl:: GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

##  <a name="domain"></a>  CSid::Domain

Devuelve el nombre del dominio asociado `CSid` al objeto.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve el `LPCTSTR` que señala al dominio.

### <a name="remarks"></a>Comentarios

Este método intenta encontrar un nombre para el (identificador `SID` de seguridad) especificado. Para obtener información completa, vea [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Si no se `SID` puede encontrar ningún nombre de cuenta para `Domain` , devuelve el dominio como una cadena vacía. Esto puede ocurrir si un tiempo de espera de red impide que este método encuentre el nombre. También se produce para los identificadores de seguridad que no tienen el nombre de cuenta `SID` correspondiente, como un que identifica una sesión de inicio de sesión.

##  <a name="equalprefix"></a>  CSid::EqualPrefix

Prefijos de pruebas `SID` (identificador de seguridad) para la igualdad.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
La `SID` estructura o `CSid` el objeto (identificador de seguridad) que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Consulte [EqualPrefixSid](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) en el Windows SDK para obtener más información.

##  <a name="getlength"></a>  CSid::GetLength

Devuelve la longitud del `CSid` objeto.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud en bytes del `CSid` objeto.

### <a name="remarks"></a>Comentarios

Si la `CSid` estructura no es válida, el valor devuelto es indefinido. Antes de `GetLength`llamar a, utilice la función miembro [CSid:: IsValid](#isvalid) para `CSid` comprobar que es válida.

> [!NOTE]
>  En depurar compilaciones, la función producirá una aserción si el `CSid` objeto no es válido.

##  <a name="getpsid"></a>  CSid::GetPSID

Devuelve un puntero a una `SID` estructura (identificador de seguridad).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección de la `CSid` estructura subyacente `SID` del objeto.

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

Devuelve un puntero a la `SID_IDENTIFIER_AUTHORITY` estructura.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, devuelve la dirección de la `SID_IDENTIFIER_AUTHORITY` estructura. Si se produce un error, el valor devuelto es indefinido. Se puede producir un error `CSid` si el objeto no es válido, en cuyo caso el método [CSid:: IsValid](#isvalid) devuelve false. Se puede `GetLastError` llamar a la función para obtener información de error extendida.

> [!NOTE]
>  En depurar compilaciones, la función producirá una aserción si el `CSid` objeto no es válido.

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

Devuelve un subautor especificado en una `SID` estructura (identificador de seguridad).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parámetros

*nSubAuthority*<br/>
El subautor.

### <a name="return-value"></a>Valor devuelto

Devuelve el subautor al que hace referencia *nSubAuthority.* El valor de subautoridad es un identificador relativo (RID).

### <a name="remarks"></a>Comentarios

El parámetro *nSubAuthority* especifica un valor de índice que identifica el elemento de matriz de subautor que el método devolverá. El método no realiza ninguna prueba de validación en este valor. Una aplicación puede llamar a [CSid:: GetSubAuthorityCount](#getsubauthoritycount) para detectar el intervalo de valores aceptables.

> [!NOTE]
>  En depurar compilaciones, la función producirá una aserción si el `CSid` objeto no es válido.

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

Devuelve el recuento de subautoridad.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es el recuento de subautoridad.

Si se produce un error en el método, el valor devuelto es indefinido. El método genera un error `CSid` si el objeto no es válido. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

> [!NOTE]
>  En depurar compilaciones, la función producirá una aserción si el `CSid` objeto no es válido.

##  <a name="isvalid"></a>  CSid::IsValid

Comprueba la `CSid` validez del objeto.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el `CSid` objeto es válido, false en caso contrario. No hay información de error extendida para este método; no llame a `GetLastError`.

### <a name="remarks"></a>Comentarios

El `IsValid` método valida el `CSid` objeto comprobando que el número de revisión está dentro de un intervalo conocido y que el número de subautores es menor que el máximo.

##  <a name="loadaccount"></a>  CSid::LoadAccount

Actualiza el `CSid` objeto dado el nombre de cuenta y el dominio, o una estructura de SID (identificador de seguridad) existente.

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
El nombre de la cuenta.

*pszSystem*<br/>
Nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se utiliza en su lugar el sistema local.

*pSid*<br/>
Puntero a una estructura de [SID](/windows/desktop/api/winnt/ns-winnt-sid) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Comentarios

`LoadAccount`intenta buscar un identificador de seguridad para el nombre especificado. Vea [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida) para obtener más detalles.

##  <a name="operator_eq"></a>CSid:: Operator =

Operador de asignación.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
(Identificador de seguridad) o `CSid` que se va a asignar `CSid` al objeto. `SID`

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto actualizado `CSid` .

##  <a name="operator_eq_eq"></a>CSid:: Operator = =

Comprueba la igualdad de dos objetos de descriptor de seguridad.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador = =. `SID`

*rhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado derecho del operador = =. `SID`

### <a name="return-value"></a>Valor devuelto

TRUE si los descriptores de seguridad son iguales; en caso contrario, FALSE.

##  <a name="operator_neq"></a>CSid:: Operator! =

Comprueba si dos objetos de descriptor de seguridad no son iguales.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador! =. `SID`

*rhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado derecho del operador! =. `SID`

### <a name="return-value"></a>Valor devuelto

TRUE si los descriptores de seguridad no son iguales; de lo contrario, FALSE.

##  <a name="operator_lt"></a>CSid:: Operator&lt;

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador! =. `SID`

*rhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado derecho del operador! =. `SID`

### <a name="return-value"></a>Valor devuelto

TRUE si *LHS* es menor que *RHS*; de lo contrario, false.

##  <a name="operator_lt__eq"></a>CSid:: Operator&lt;=

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador! =. `SID`

*rhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado derecho del operador! =. `SID`

### <a name="return-value"></a>Valor devuelto

TRUE si *LHS* es menor o igual que *RHS*; de lo contrario, false.

##  <a name="operator_gt"></a>CSid:: Operator&gt;

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador! =. `SID`

*rhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado derecho del operador! =. `SID`

### <a name="return-value"></a>Valor devuelto

TRUE si *LHS* es mayor que *RHS*; de lo contrario, false.

##  <a name="operator_gt__eq"></a>CSid:: Operator&gt;=

Compara el valor relativo de dos objetos de descriptor de seguridad.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado izquierdo del operador! =. `SID`

*rhs*<br/>
(Identificador de seguridad) o `CSid` que aparece en el lado derecho del operador! =. `SID`

### <a name="return-value"></a>Valor devuelto

TRUE si *LHS* es mayor o igual que *RHS*; de lo contrario, false.

##  <a name="operator_const_sid__star"></a>CSid:: Operator const SID\*

Convierte un `CSid` objeto en un puntero a una estructura `SID` (identificador de seguridad).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Devuelve la dirección de la `SID` estructura.

##  <a name="sid"></a>  CSid::Sid

Devuelve la `SID` estructura (identificador de seguridad) como una cadena.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve la `SID` estructura como una cadena en un formato adecuado para la presentación, el almacenamiento o la transmisión. Equivalente a [ConvertSidToStringSid](/windows/desktop/api/sddl/nf-sddl-convertsidtostringsida).

##  <a name="sidnameuse"></a>  CSid::SidNameUse

Devuelve una descripción del estado del `CSid` objeto.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del miembro de datos que almacena un valor que describe el estado del `CSid` objeto.

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|SidTypeUser|Indica un usuario `SID` (identificador de seguridad).|
|SidTypeGroup|Indica un grupo `SID`.|
|SidTypeDomain|Indica un dominio `SID`.|
|SidTypeAlias|Indica un alias `SID`.|
|SidTypeWellKnownGroup|Indica un `SID` para un grupo conocido.|
|SidTypeDeletedAccount|Indica un `SID` para una cuenta eliminada.|
|SidTypeInvalid|Indica un no `SID`válido.|
|SidTypeUnknown|Indica un tipo `SID` desconocido.|
|SidTypeComputer|Indica un `SID` para un equipo.|

### <a name="remarks"></a>Comentarios

Llame a [CSid:: LoadAccount](#loadaccount) para actualizar `CSid` el objeto antes `SidNameUse` de llamar a para devolver su estado. `SidNameUse`no cambia el estado del objeto (llamando a `LookupAccountName` o `LookupAccountSid`), pero solo devuelve el estado actual.

## <a name="see-also"></a>Vea también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)<br/>
[Operadores](../../atl/reference/atl-operators.md)
