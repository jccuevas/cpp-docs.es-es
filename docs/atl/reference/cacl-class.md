---
title: Clase CAcl
ms.date: 11/04/2016
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: 5d03154597f800042846e82d0a0cf5e7c46b613f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423511"
---
# <a name="cacl-class"></a>Clase CAcl

Esta clase es un contenedor para una estructura de `ACL` (lista de control de acceso).

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAcl
```

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Matriz de ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Matriz de BYTEs.|
|[CAcl::CAceTypeArray](#cacetypearray)|Matriz de BYTEs.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|El constructor.|
|[CAcl:: ~ CAcl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Devuelve el número de objetos de entrada de control de acceso (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Recupera las entradas de la lista de control de acceso (ACL) del objeto `CAcl`.|
|[CAcl::GetAclEntry](#getaclentry)|Recupera toda la información sobre una entrada de un objeto `CAcl`.|
|[CAcl:: GetLength](#getlength)|Devuelve la longitud de la ACL.|
|[CAcl::GetPACL](#getpacl)|Devuelve un paquetes (puntero a una ACL).|
|[CAcl:: IsEmpty](#isempty)|Comprueba si hay entradas en el objeto de `CAcl`.|
|[CAcl:: IsNull](#isnull)|Devuelve el estado del objeto `CAcl`.|
|[CAcl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) del objeto `CAcl`.|
|[CAcl::RemoveAces](#removeaces)|Quita todas las ACE (entradas de control de acceso) del `CAcl` que se aplican a la `CSid`especificada.|
|[CAcl::SetEmpty](#setempty)|Marca el objeto de `CAcl` como vacío.|
|[CAcl:: SetNull](#setnull)|Marca el objeto de `CAcl` como NULL.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAcl:: Operator const ACL *](#operator_const_acl__star)|Convierte un objeto de `CAcl` en una estructura de `ACL`.|
|[CAcl:: Operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

La estructura `ACL` es el encabezado de una ACL (lista de control de acceso). Una ACL incluye una lista secuencial de cero o más [ACE](/windows/win32/SecAuthZ/access-control-entries) (entradas de control de acceso). Las ACE individuales de una ACL se numeran de 0 a *n-1*, donde *n* es el número de ACE de la ACL. Al editar una ACL, una aplicación hace referencia a una entrada de control de acceso (ACE) dentro de la ACL por su índice.

Hay dos tipos de ACL:

- Discrecional

- Sistema

Un ACL discrecional se controla mediante el propietario de un objeto o cualquier persona concedido WRITE_DAC acceso al objeto. Especifica que los usuarios y grupos específicos de Access pueden tener un objeto. Por ejemplo, el propietario de un archivo puede utilizar una ACL discrecional para controlar qué usuarios y grupos pueden y no pueden tener acceso al archivo.

Un objeto también puede tener asociada información de seguridad de nivel de sistema, en forma de una ACL del sistema controlada por un administrador del sistema. Una ACL del sistema puede permitir al administrador del sistema auditar cualquier intento de obtener acceso a un objeto.

Para obtener más información, consulte la explicación de la [ACL](/windows/win32/SecAuthZ/access-control-lists) en el Windows SDK.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Matriz de objetos ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Observaciones

Este typedef especifica el tipo de matriz que se puede usar para almacenar derechos de acceso utilizados en entradas de control de acceso (ACE).

##  <a name="caceflagarray"></a>CAcl::CAceFlagArray

Matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Observaciones

Este typedef especifica el tipo de matriz que se usa para definir las marcas de control específicas del tipo de entrada de control de acceso (ACE). Consulte la definición de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para ver la lista completa de posibles marcas.

##  <a name="cacetypearray"></a>CAcl::CAceTypeArray

Matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Observaciones

Este typedef especifica el tipo de matriz que se usa para definir la naturaleza de los objetos de entrada de control de acceso (ACE), como ACCESS_ALLOWED_ACE_TYPE o ACCESS_DENIED_ACE_TYPE. Consulte la definición de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener una lista completa de los tipos posibles.

##  <a name="cacl"></a>CAcl::CAcl

El constructor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CAcl` existente.

### <a name="remarks"></a>Observaciones

El objeto `CAcl` se puede crear opcionalmente con un objeto `CAcl` existente.

##  <a name="dtor"></a>CAcl:: ~ CAcl

Destructor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos adquiridos por el objeto.

##  <a name="getacecount"></a>CAcl::GetAceCount

Devuelve el número de objetos de entrada de control de acceso (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de entradas ACE en el objeto `CAcl`.

##  <a name="getaclentries"></a>CAcl::GetAclEntries

Recupera las entradas de la lista de control de acceso (ACL) del objeto `CAcl`.

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSids*<br/>
Puntero a una matriz de objetos [CSid](../../atl/reference/csid-class.md) .

*pAccessMasks*<br/>
Las máscaras de acceso.

*pAceTypes*<br/>
Los tipos de entrada de control de acceso (ACE).

*pAceFlags*<br/>
Marcas ACE.

### <a name="remarks"></a>Observaciones

Este método rellena los parámetros de la matriz con los detalles de todos los objetos ACE contenidos en el objeto `CAcl`. Use NULL cuando no se requieran los detalles de esa matriz en particular.

El contenido de cada matriz se corresponde entre sí, es decir, el primer elemento de la matriz de `CAccessMaskArray` corresponde al primer elemento de la matriz de `CSidArray`, etc.

Consulte [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener más detalles sobre los tipos ACE y las marcas.

##  <a name="getaclentry"></a>CAcl::GetAclEntry

Recupera toda la información sobre una entrada de una lista de control de acceso (ACL).

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

*nIndex*<br/>
Índice de la entrada de ACL que se va a recuperar.

*pSid*<br/>
Objeto [CSid](../../atl/reference/csid-class.md) al que se aplica la entrada ACL.

*pMask*<br/>
Máscara que especifica los permisos para conceder o denegar el acceso.

*pType*<br/>
Tipo de ACE.

*pFlags*<br/>
Marcas ACE.

*pObjectType*<br/>
El tipo de objeto. Se establecerá en GUID_NULL si el tipo de objeto no se especifica en la ACE, o si la ACE no es una ACE de objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado. Se establecerá en GUID_NULL si el tipo de objeto heredado no se especifica en la ACE, o si la ACE no es una ACE de objeto.

### <a name="remarks"></a>Observaciones

Este método recuperará toda la información sobre una ACE individual, lo que proporciona más información de la que [CAcl:: GetAclEntries](#getaclentries) solo pone a su disposición.

Consulte [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener más detalles sobre los tipos ACE y las marcas.

##  <a name="getlength"></a>CAcl:: GetLength

Devuelve la longitud de la lista de control de acceso (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud necesaria en bytes necesaria para contener la estructura de `ACL`.

##  <a name="getpacl"></a>CAcl::GetPACL

Devuelve un puntero a una lista de control de acceso (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la estructura de `ACL`.

##  <a name="isempty"></a>CAcl:: IsEmpty

Comprueba si hay entradas en el objeto de `CAcl`.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve TRUE si el objeto `CAcl` no es NULL y no contiene ninguna entrada. Devuelve FALSE si el objeto `CAcl` es NULL o contiene al menos una entrada.

##  <a name="isnull"></a>CAcl:: IsNull

Devuelve el estado del objeto `CAcl`.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el objeto `CAcl` es NULL, de lo contrario, es FALSE.

##  <a name="operator_const_acl__star"></a>CAcl:: Operator const ACL *

Convierte un objeto `CAcl` en una estructura `ACL` (lista de control de acceso).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Observaciones

Devuelve la dirección de la estructura de `ACL`.

##  <a name="operator_eq"></a>CAcl:: Operator =

Operador de asignación.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
`CAcl` que se va a asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto `CAcl` actualizado.

##  <a name="removeace"></a>CAcl::RemoveAce

Quita una ACE específica (entrada de control de acceso) del objeto `CAcl`.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la entrada ACE que se va a quitar.

### <a name="remarks"></a>Observaciones

Este método se deriva de [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>CAcl::RemoveAces

Quita las ACE de Alls (entradas de control de acceso) del `CAcl` que se aplican a la `CSid`especificada.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Referencia a un objeto `CSid`.

##  <a name="setempty"></a>CAcl::SetEmpty

Marca el objeto de `CAcl` como vacío.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Observaciones

El `CAcl` se puede establecer en Empty o en NULL: los dos Estados son distintos.

##  <a name="setnull"></a>CAcl:: SetNull

Marca el objeto de `CAcl` como NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Observaciones

El `CAcl` se puede establecer en Empty o en NULL: los dos Estados son distintos.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
