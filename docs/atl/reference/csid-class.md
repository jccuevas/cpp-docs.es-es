---
title: Clase CSid
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
ms.openlocfilehash: 414cf428cebe8105d90b3add93cc7f1e76927c2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330923"
---
# <a name="csid-class"></a>Clase CSid

Esta clase es un `SID` contenedor para una estructura (identificador de seguridad).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CSid
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Una matriz de objetos `CSid`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSid::CSid](#csid)|El constructor.|
|[CSid::-CSid](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Devuelve el nombre de la `CSid` cuenta asociada al objeto.|
|[CSid::Domain](#domain)|Devuelve el nombre del dominio `CSid` asociado al objeto.|
|[CSid::EqualPrefix](#equalprefix)|Valora los `SID` prefijos de igualdad (identificador de seguridad).|
|[CSid::GetLength](#getlength)|Devuelve la longitud `CSid` del objeto.|
|[CSid::GetPSID](#getpsid)|Devuelve un puntero `SID` a una estructura.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Devuelve un puntero `SID_IDENTIFIER_AUTHORITY` a la estructura.|
|[CSid::GetSubAuthority](#getsubauthority)|Devuelve una subautoridad especificada `SID` en una estructura.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Devuelve el recuento de subautoridades.|
|[CSid::IsValid](#isvalid)|Comprueba `CSid` la validez del objeto.|
|[CSid::LoadAccount](#loadaccount)|Actualiza `CSid` el objeto dado el nombre de `SID` cuenta y el dominio, o una estructura existente.|
|[CSid::Sid](#sid)|Devuelve la cadena de identificador.|
|[CSid::SidNameUse](#sidnameuse)|Devuelve una descripción del `CSid` estado del objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador a la operadora de la red](#operator_eq)|Operador de asignación.|
|[operador const SID *](#operator_const_sid__star)|Convierte un `CSid` objeto en un `SID` puntero a una estructura.|

### <a name="global-operators"></a>Operadores globales

|||
|-|-|
|[operador ?](#operator_eq_eq)|Prueba la igualdad de dos objetos descriptores de seguridad|
|[operador !-](#operator_neq)|Prueba dos objetos descriptores de seguridad para la desigualdad|
|[Operador\<](#operator_lt)|Compara el valor relativo de dos objetos descriptores de seguridad.|
|[operador >](#operator_gt)|Compara el valor relativo de dos objetos descriptores de seguridad.|
|[Operador\<=](#operator_lt__eq)|Compara el valor relativo de dos objetos descriptores de seguridad.|
|[>del operador ( operador)](#operator_gt__eq)|Compara el valor relativo de dos objetos descriptores de seguridad.|

## <a name="remarks"></a>Observaciones

La `SID` estructura es una estructura de longitud variable que se utiliza para identificar de forma única a usuarios o grupos.

Las aplicaciones no `SID` deben modificar la estructura directamente, sino usar los métodos proporcionados en esta clase contenedora. Vea también [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)y [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="csidaccountname"></a><a name="accountname"></a>CSid::AccountName

Devuelve el nombre de la `CSid` cuenta asociada al objeto.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve el LPCTSTR que apunta al nombre de la cuenta.

### <a name="remarks"></a>Observaciones

Este método intenta encontrar un nombre `SID` para el especificado (identificador de seguridad). Para obtener más información, consulte [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Si no se `SID` puede encontrar `AccountName` ningún nombre de cuenta para el, devuelve una cadena vacía. Esto puede ocurrir si un tiempo de espera de red impide que este método encuentre el nombre. También se produce para los identificadores de seguridad `SID` sin el nombre de cuenta correspondiente, como un que identifica una sesión de inicio de sesión.

## <a name="csidcsid"></a><a name="csid"></a>CSid::CSid

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
Un `CSid` objeto `SID` existente o (identificador de seguridad) estructura.

*IdentifierAuthority*<br/>
La autoridad.

*nSubAuthorityCount*<br/>
El recuento de subautoridades.

*pszAccountName*<br/>
Nombre de cuenta

*pszSystem*<br/>
El nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se usa el sistema local en su lugar.

*Psid*<br/>
Un puntero `SID` a una estructura.

### <a name="remarks"></a>Observaciones

El constructor inicializa `CSid` el objeto, estableciendo un miembro de datos interno en *SidTypeInvalid*o copiando la configuración de una cuenta existente, `CSid` `SID`o existente.

Si se produce un error en la inicialización, el constructor producirá una [clase CAtlException](../../atl/reference/catlexception-class.md).

## <a name="csidcsid"></a><a name="dtor"></a>CSid::-CSid

Destructor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos adquiridos por el objeto.

## <a name="csidcsidarray"></a><a name="csidarray"></a>CSid::CSidArray

Matriz de objetos [CSid.](../../atl/reference/csid-class.md)

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Observaciones

Este typedef especifica el tipo de matriz que se puede utilizar para recuperar identificadores de seguridad de una ACL (lista de control de acceso). Consulte [CAcl::GetaclEntries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a>CSid::Domain

Devuelve el nombre del dominio `CSid` asociado al objeto.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve `LPCTSTR` el que apunta al dominio.

### <a name="remarks"></a>Observaciones

Este método intenta encontrar un nombre `SID` para el especificado (identificador de seguridad). Para obtener más información, consulte [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Si no se `SID` encuentra ningún `Domain` nombre de cuenta para el, devuelve el dominio como una cadena vacía. Esto puede ocurrir si un tiempo de espera de red impide que este método encuentre el nombre. También se produce para los identificadores de seguridad `SID` sin el nombre de cuenta correspondiente, como un que identifica una sesión de inicio de sesión.

## <a name="csidequalprefix"></a><a name="equalprefix"></a>CSid::EqualPrefix

Valora los `SID` prefijos de igualdad (identificador de seguridad).

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
La `SID` estructura u `CSid` objeto (identificador de seguridad) que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Consulte [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) en el Windows SDK para obtener más detalles.

## <a name="csidgetlength"></a><a name="getlength"></a>CSid::GetLength

Devuelve la longitud `CSid` del objeto.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud en `CSid` bytes del objeto.

### <a name="remarks"></a>Observaciones

Si `CSid` la estructura no es válida, el valor devuelto es indefinido. Antes `GetLength`de llamar a , utilice la [CSid::IsValid](#isvalid) función miembro para comprobar que `CSid` es válido.

> [!NOTE]
> En compilaciones de depuración, la `CSid` función provocará un ASSERT si el objeto no es válido.

## <a name="csidgetpsid"></a><a name="getpsid"></a>CSid::GetPSID

Devuelve un puntero `SID` a una estructura (identificador de seguridad).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección `CSid` de la `SID` estructura subyacente del objeto.

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY

Devuelve un puntero `SID_IDENTIFIER_AUTHORITY` a la estructura.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, `SID_IDENTIFIER_AUTHORITY` devuelve la dirección de la estructura. Si se produce un error, el valor devuelto es indefinido. Se puede producir `CSid` un error si el objeto no es válido, en cuyo caso el [CSid::IsValid](#isvalid) método devuelve FALSE. Se `GetLastError` puede llamar a la función para obtener información de error ampliada.

> [!NOTE]
> En compilaciones de depuración, la `CSid` función provocará un ASSERT si el objeto no es válido.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a>CSid::GetSubAuthority

Devuelve una subautoridad especificada `SID` en una estructura (identificador de seguridad).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parámetros

*nSubautoridad*<br/>
La subautoridad.

### <a name="return-value"></a>Valor devuelto

Devuelve la subautoridad a la que hace referencia *nSubAuthority.* El valor de subautoridad es un identificador relativo (RID).

### <a name="remarks"></a>Observaciones

El *nSubAuthority* parámetro especifica un valor de índice que identifica el elemento de matriz de subautoridad que el método devolverá. El método no realiza ninguna prueba de validación en este valor. Una aplicación puede llamar a [CSid::GetSubAuthorityCount](#getsubauthoritycount) para detectar el intervalo de valores aceptables.

> [!NOTE]
> En compilaciones de depuración, la `CSid` función provocará un ASSERT si el objeto no es válido.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount

Devuelve el recuento de subautoridades.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto es el recuento de subautoridades.

Si se produce un error en el método, el valor devuelto es indefinido. Se produce un `CSid` error en el método si el objeto no es válido. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

> [!NOTE]
> En compilaciones de depuración, la `CSid` función provocará un ASSERT si el objeto no es válido.

## <a name="csidisvalid"></a><a name="isvalid"></a>CSid::IsValid

Comprueba `CSid` la validez del objeto.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE `CSid` si el objeto es válido, FALSE si no. No hay información de error extendida para este método; no llame `GetLastError`a .

### <a name="remarks"></a>Observaciones

El `IsValid` método valida `CSid` el objeto comprobando que el número de revisión está dentro de un intervalo conocido y que el número de subautoridades es menor que el máximo.

## <a name="csidloadaccount"></a><a name="loadaccount"></a>CSid::LoadAccount

Actualiza `CSid` el objeto dado el nombre de cuenta y el dominio, o una estructura SID (identificador de seguridad) existente.

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
Nombre de cuenta

*pszSystem*<br/>
El nombre del sistema. Esta cadena puede ser el nombre de un equipo remoto. Si esta cadena es NULL, se usa el sistema local en su lugar.

*Psid*<br/>
Un puntero a una estructura [SID.](/windows/win32/api/winnt/ns-winnt-sid)

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Observaciones

`LoadAccount`intenta encontrar un identificador de seguridad para el nombre especificado. Consulte [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) para obtener más detalles.

## <a name="csidoperator-"></a><a name="operator_eq"></a>CSid::operador ?

Operador de asignación.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
El `SID` (identificador de `CSid` seguridad) `CSid` o para asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia `CSid` al objeto actualizado.

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a>CSid::operador ?

Prueba la igualdad de dos objetos descriptores de seguridad.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado izquierdo del operador .

*rhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado derecho del operador .

### <a name="return-value"></a>Valor devuelto

TRUESi los descriptores de seguridad son iguales, de lo contrario FALSE.

## <a name="csidoperator-"></a><a name="operator_neq"></a>CSid::operador !-

Prueba dos objetos descriptores de seguridad para la desigualdad.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado izquierdo del operador !.

*rhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado derecho del operador !.

### <a name="return-value"></a>Valor devuelto

TRUESi los descriptores de seguridad no son iguales, en caso contrario FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a>CSid::operador&lt;

Compara el valor relativo de dos objetos descriptores de seguridad.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado izquierdo del operador !.

*rhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado derecho del operador !.

### <a name="return-value"></a>Valor devuelto

TRUESi *lhs* es menor que *rhs*, de lo contrario FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid::operador&lt;=

Compara el valor relativo de dos objetos descriptores de seguridad.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado izquierdo del operador !.

*rhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado derecho del operador !.

### <a name="return-value"></a>Valor devuelto

TRUESi *lhs* es menor o igual que *rhs*, de lo contrario FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a>CSid::operador&gt;

Compara el valor relativo de dos objetos descriptores de seguridad.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado izquierdo del operador !.

*rhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado derecho del operador !.

### <a name="return-value"></a>Valor devuelto

TRUESi *lhs* es mayor que *rhs*, de lo contrario FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid::operador&gt;=

Compara el valor relativo de dos objetos descriptores de seguridad.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado izquierdo del operador !.

*rhs*<br/>
El `SID` (identificador de `CSid` seguridad) o que aparece en el lado derecho del operador !.

### <a name="return-value"></a>Valor devuelto

TRUESi *lhs* es mayor o igual que *rhs*, de lo contrario FALSE.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid::operator const SID\*

Convierte un `CSid` objeto en un `SID` puntero a una estructura (identificador de seguridad).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Observaciones

Devuelve la dirección `SID` de la estructura.

## <a name="csidsid"></a><a name="sid"></a>CSid::Sid

Devuelve `SID` la estructura (identificador de seguridad) como una cadena.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve `SID` la estructura como una cadena en un formato adecuado para la visualización, el almacenamiento o la transmisión. Equivalente a [ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a>CSid::SidNameUse

Devuelve una descripción del `CSid` estado del objeto.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del miembro de datos que almacena `CSid` un valor que describe el estado del objeto.

|Value|Descripción|
|-----------|-----------------|
|SidTypeUser|Indica un `SID` usuario (identificador de seguridad).|
|SidTypeGroup|Indica un `SID`grupo .|
|SidTypeDomain|Indica un `SID`dominio .|
|SidTypeAlias|Indica un `SID`alias .|
|SidTypeWellKnownGroup|Indica un `SID` grupo conocido.|
|SidTypeDeletedAccount|Indica un `SID` para una cuenta eliminada.|
|SidTypeInvalid|Indica un `SID`archivo .|
|SidTypeUnknown|Indica un `SID` tipo desconocido.|
|SidTypeComputer|Indica a `SID` para un equipo.|

### <a name="remarks"></a>Observaciones

Llame a [CSid::LoadAccount](#loadaccount) para actualizar el `CSid` objeto antes de llamar `SidNameUse` para devolver su estado. `SidNameUse`no cambia el estado del objeto `LookupAccountName` (llamando a o `LookupAccountSid`), sino que solo devuelve el estado actual.

## <a name="see-also"></a>Consulte también

[Ejemplo de seguridad](../../overview/visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)<br/>
[Operadores](../../atl/reference/atl-operators.md)
