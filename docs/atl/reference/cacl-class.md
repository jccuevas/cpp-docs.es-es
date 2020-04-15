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
ms.openlocfilehash: 87bf903220a584798ea59c5f1c701fc35049e901
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321660"
---
# <a name="cacl-class"></a>Clase CAcl

Esta clase es un `ACL` contenedor para una estructura (lista de control de acceso).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAcl
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Una matriz de ACCESS_MASKs.|
|[Cacl::CaceFlagArray](#caceflagarray)|Una matriz de BYTEs.|
|[CAcl::CaceTypeArray](#cacetypearray)|Una matriz de BYTEs.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|El constructor.|
|[CAcl::-Cacl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cacl::GetaceCount](#getacecount)|Devuelve el número de objetos de entrada de control de acceso (ACE).|
|[Cacl::GetaclEntries](#getaclentries)|Recupera las entradas de la lista de `CAcl` control de acceso (ACL) del objeto.|
|[CAcl::GetAclEntry](#getaclentry)|Recupera toda la información sobre una `CAcl` entrada en un objeto.|
|[CAcl::GetLength](#getlength)|Devuelve la longitud de la ACL.|
|[CAcl::GetPACL](#getpacl)|Devuelve un PACL (puntero a una ACL).|
|[CAcl::IsEmpty](#isempty)|Comprueba `CAcl` el objeto en busca de entradas.|
|[Cacl::IsNull](#isnull)|Devuelve el estado `CAcl` del objeto.|
|[Cacl::Removeace](#removeace)|Quita un ACE específico (entrada de `CAcl` control de acceso) del objeto.|
|[CAcl::RemoveAces](#removeaces)|Quita todas las ACE (entradas de control `CAcl` de acceso) `CSid`de las que se aplican a la dada.|
|[CAcl::SetEmpty](#setempty)|Marca `CAcl` el objeto como vacío.|
|[CAcl::SetNull](#setnull)|Marca `CAcl` el objeto como NULL.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAcl::operator const ACL *](#operator_const_acl__star)|Convierte un `CAcl` objeto `ACL` en una estructura.|
|[CAcl::operador ?](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

La `ACL` estructura es el encabezado de un ACL (lista de control de acceso). Una ACL incluye una lista secuencial de cero o más [ACE](/windows/win32/SecAuthZ/access-control-entries) (entradas de control de acceso). Las ACE individuales en un ACL se numeran de 0 a *n-1,* donde *n* es el número de ACE en el ACL. Al editar una ACL, una aplicación hace referencia a una entrada de control de acceso (ACE) dentro de la ACL por su índice.

Hay dos tipos ACL:

- Discrecional

- Sistema

Una ACL discrecional es controlada por el propietario de un objeto o cualquier persona a la que se le conceda WRITE_DAC acceso al objeto. Especifica el acceso que los usuarios y grupos concretos pueden tener a un objeto. Por ejemplo, el propietario de un archivo puede utilizar una ACL discrecional para controlar qué usuarios y grupos pueden y no pueden tener acceso al archivo.

Un objeto también puede tener información de seguridad de nivel de sistema asociada, en forma de una ACL del sistema controlada por un administrador del sistema. Una ACL del sistema puede permitir que el administrador del sistema audite cualquier intento de obtener acceso a un objeto.

Para obtener más información, consulte la explicación de [ACL](/windows/win32/SecAuthZ/access-control-lists) en el Windows SDK.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Matriz de objetos ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Observaciones

Este typedef especifica el tipo de matriz que se puede utilizar para almacenar los derechos de acceso utilizados en las entradas de control de acceso (ACE).

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>Cacl::CaceFlagArray

Una matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Observaciones

Este typedef especifica el tipo de matriz utilizado para definir los indicadores de control específicos de tipo de entrada de control de acceso (ACE). Consulte la [definición](/windows/win32/api/winnt/ns-winnt-ace_header) de ACE_HEADER para obtener la lista completa de indicadores posibles.

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CaceTypeArray

Una matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Observaciones

Este typedef especifica el tipo de matriz utilizado para definir la naturaleza de los objetos de entrada de control de acceso (ACE), como ACCESS_ALLOWED_ACE_TYPE o ACCESS_DENIED_ACE_TYPE. Consulte la definición [de ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener la lista completa de tipos posibles.

## <a name="caclcacl"></a><a name="cacl"></a>CAcl::CAcl

El constructor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CAcl` existente.

### <a name="remarks"></a>Observaciones

El `CAcl` objeto se puede crear `CAcl` opcionalmente utilizando un objeto existente.

## <a name="caclcacl"></a><a name="dtor"></a>CAcl::-Cacl

Destructor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Observaciones

El destructor libera todos los recursos adquiridos por el objeto.

## <a name="caclgetacecount"></a><a name="getacecount"></a>Cacl::GetaceCount

Devuelve el número de objetos de entrada de control de acceso (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de entradas `CAcl` ACE en el objeto.

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>Cacl::GetaclEntries

Recupera las entradas de la lista de `CAcl` control de acceso (ACL) del objeto.

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSids*<br/>
Puntero a una matriz de [CSid](../../atl/reference/csid-class.md) objetos.

*pAccessMasks*<br/>
Las máscaras de acceso.

*pAceTypes*<br/>
Los tipos de entrada de control de acceso (ACE).

*pAceFlags*<br/>
Las banderas ACE.

### <a name="remarks"></a>Observaciones

Este método rellena los parámetros de matriz con los `CAcl` detalles de cada objeto ACE contenido en el objeto. Use NULL cuando no se requieran los detalles de esa matriz en particular.

El contenido de cada matriz se corresponde entre sí, `CAccessMaskArray` es decir, el primer `CSidArray` elemento de la matriz corresponde al primer elemento de la matriz, etc.

Consulte [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener más detalles sobre los tipos y indicadores ACE.

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>CAcl::GetAclEntry

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

*nIndex*<br/>
Indice a la entrada ACL que se va a recuperar.

*Psid*<br/>
El objeto [CSid](../../atl/reference/csid-class.md) al que se aplica la entrada ACL.

*pMask*<br/>
La máscara que especifica permisos para conceder o denegar el acceso.

*pType*<br/>
El tipo ACE.

*pFlags*<br/>
Las banderas ACE.

*pObjectType*<br/>
El tipo de objeto. Esto se establecerá en GUID_NULL si el tipo de objeto no se especifica en la ACE, o si la ACE no es una ACE DE OBJETO.

*pInheritedObjectType*<br/>
El tipo de objeto heredado. Esto se establecerá en GUID_NULL si el tipo de objeto heredado no se especifica en la ACE, o si la ACE no es una ACE DE OBJETO.

### <a name="remarks"></a>Observaciones

Este método recuperará toda la información sobre una ACE individual, proporcionando más información que [CAcl::GetAclEntries](#getaclentries) por sí solo hace disponible.

Consulte [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener más detalles sobre los tipos y indicadores ACE.

## <a name="caclgetlength"></a><a name="getlength"></a>CAcl::GetLength

Devuelve la longitud de la lista de control de acceso (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud necesaria en `ACL` bytes necesario para contener la estructura.

## <a name="caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL

Devuelve un puntero a una lista de control de acceso (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `ACL` a la estructura.

## <a name="caclisempty"></a><a name="isempty"></a>CAcl::IsEmpty

Comprueba `CAcl` el objeto en busca de entradas.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve TRUE `CAcl` si el objeto no es NULL y no contiene ninguna entrada. Devuelve FALSE `CAcl` si el objeto es NULL o contiene al menos una entrada.

## <a name="caclisnull"></a><a name="isnull"></a>Cacl::IsNull

Devuelve el estado `CAcl` del objeto.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE `CAcl` si el objeto es NULL, FALSE en caso contrario.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CAcl::operator const ACL *

Convierte un `CAcl` objeto `ACL` en una estructura (lista de control de acceso).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Observaciones

Devuelve la dirección `ACL` de la estructura.

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl::operador ?

Operador de asignación.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
El `CAcl` para asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia `CAcl` al objeto actualizado.

## <a name="caclremoveace"></a><a name="removeace"></a>Cacl::Removeace

Quita un ACE específico (entrada de `CAcl` control de acceso) del objeto.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice a la entrada ACE que se va a quitar.

### <a name="remarks"></a>Observaciones

Este método se deriva de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces

Quita todas las ACE (entradas de control `CAcl` de acceso) `CSid`de las que se aplican a la dada.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Referencia a un objeto `CSid`.

## <a name="caclsetempty"></a><a name="setempty"></a>CAcl::SetEmpty

Marca `CAcl` el objeto como vacío.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Observaciones

Se `CAcl` puede establecer en empty o NULL: los dos estados son distintos.

## <a name="caclsetnull"></a><a name="setnull"></a>CAcl::SetNull

Marca `CAcl` el objeto como NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Observaciones

Se `CAcl` puede establecer en empty o NULL: los dos estados son distintos.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
