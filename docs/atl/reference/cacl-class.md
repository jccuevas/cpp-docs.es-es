---
title: CAcl (clase)
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
ms.openlocfilehash: a9653225f3057d6c5ba9fd49cf64487e766ca8d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491551"
---
# <a name="cacl-class"></a>CAcl (clase)

Esta clase es un contenedor para un `ACL` estructura (lista de control de acceso).

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAcl
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Una matriz de ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Una matriz de BYTEs.|
|[CAcl::CAceTypeArray](#cacetypearray)|Una matriz de BYTEs.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|El constructor.|
|[CAcl:: ~ CAcl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Devuelve al número de control de acceso a objetos de entrada (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Recupera las entradas de control de acceso (ACL) de la lista de los `CAcl` objeto.|
|[CAcl::GetAclEntry](#getaclentry)|Recupera toda la información sobre una entrada en un `CAcl` objeto.|
|[CAcl::GetLength](#getlength)|Devuelve la longitud de la ACL.|
|[CAcl::GetPACL](#getpacl)|Devuelve un paquetes (puntero a una ACL).|
|[CAcl::IsEmpty](#isempty)|Las pruebas del `CAcl` objeto para las entradas.|
|[CAcl::IsNull](#isnull)|Devuelve el estado de la `CAcl` objeto.|
|[CAcl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) de la `CAcl` objeto.|
|[CAcl::RemoveAces](#removeaces)|Quita todas las entradas de control de acceso de la `CAcl` que se aplican a la determinada `CSid`.|
|[CAcl::SetEmpty](#setempty)|Las marcas de la `CAcl` objeto como vacío.|
|[CAcl::SetNull](#setnull)|Las marcas de la `CAcl` objeto como NULL.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[ACL de CAcl::operator const *](#operator_const_acl__star)|Convierte un `CAcl` objeto a un `ACL` estructura.|
|[CAcl::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

El `ACL` estructura es el encabezado de una ACL (lista de control de acceso). Una ACL incluye una lista secuencial de cero o más [ACE](/windows/desktop/SecAuthZ/access-control-entries) (entradas de control de acceso). Las ACE individuales en una ACL se numeran de 0 a *n-1*, donde *n* es el número de ACE en la ACL. Al modificar una ACL, una aplicación hace referencia a una entrada de control de acceso (ACE) dentro de la ACL por su índice.

Hay dos tipos ACL:

- Discrecional

- Sistema

Una ACL discrecional está controlada por el propietario de un objeto o cualquier persona concedido acceso WRITE_DAC para el objeto. Especifica el acceso a usuarios y grupos concretos que pueden tener a un objeto. Por ejemplo, el propietario de un archivo puede usar una ACL discrecional para controlar qué usuarios y grupos puede y no puede tener acceso al archivo.

Un objeto también puede tener asociada, en forma de un sistema ACL controlado por un administrador del sistema de información de seguridad de nivel de sistema. Un ACL del sistema puede permitir que el administrador del sistema auditar los intentos de obtener acceso a un objeto.

Para obtener más información, consulte el [ACL](/windows/desktop/SecAuthZ/access-control-lists) discusión en el SDK de Windows.

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="caccessmaskarray"></a>  CAcl::CAccessMaskArray

Una matriz de objetos ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Comentarios

Esta definición de tipo especifica el tipo de matriz que se puede usar para almacenar los derechos de acceso utilizados en las entradas de control de acceso (ACE).

##  <a name="caceflagarray"></a>  CAcl::CAceFlagArray

Una matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Comentarios

Esta definición de tipo especifica el tipo de matriz que se usan para definir las marcas de control específicos del tipo de control de acceso (ACE) de entrada. Consulte la [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) definición de la lista completa de marcas posible.

##  <a name="cacetypearray"></a>  CAcl::CAceTypeArray

Una matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Comentarios

Esta definición de tipo especifica el tipo de matriz que se usan para definir la naturaleza de los objetos de control de acceso (ACE) de entrada, como ACCESS_ALLOWED_ACE_TYPE o ACCESS_DENIED_ACE_TYPE. Consulte la [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) definición para obtener una lista completa de los tipos posibles.

##  <a name="cacl"></a>  CAcl::CAcl

El constructor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*RHS*<br/>
Objeto `CAcl` existente.

### <a name="remarks"></a>Comentarios

El `CAcl` objeto se puede, opcionalmente, crear una existente `CAcl` objeto.

##  <a name="dtor"></a>  CAcl:: ~ CAcl

Destructor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera los recursos adquiridos por el objeto.

##  <a name="getacecount"></a>  CAcl::GetAceCount

Devuelve al número de control de acceso a objetos de entrada (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de entradas ACE en el `CAcl` objeto.

##  <a name="getaclentries"></a>  CAcl::GetAclEntries

Recupera las entradas de control de acceso (ACL) de la lista de los `CAcl` objeto.

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSids*<br/>
Un puntero a una matriz de [CSid](../../atl/reference/csid-class.md) objetos.

*pAccessMasks*<br/>
Las máscaras de acceso.

*pAceTypes*<br/>
Los tipos de control de acceso (ACE) de entrada.

*pAceFlags*<br/>
Los indicadores ACE.

### <a name="remarks"></a>Comentarios

Este método rellena los parámetros de matriz con los detalles de todos los objetos ACE incluidos en el `CAcl` objeto. Utilice NULL cuando no se requieren los detalles de esa matriz determinado.

El contenido de cada matriz corresponde entre sí, es decir, el primer elemento de la `CAccessMaskArray` matriz corresponde al primer elemento en el `CSidArray` matriz y así sucesivamente.

Consulte [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) para obtener más detalles sobre los tipos ACE y marcas.

##  <a name="getaclentry"></a>  CAcl::GetAclEntry

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
Índice de la entrada ACL para recuperar.

*pSid*<br/>
El [CSid](../../atl/reference/csid-class.md) objeto al que se aplica la entrada ACL.

*pMask*<br/>
La máscara de especificación de permisos para conceder o denegar el acceso.

*PEscriba*<br/>
El tipo de ACE.

*pFlags*<br/>
Los indicadores ACE.

*pObjectType*<br/>
Tipo del objeto. Esto se establecerá en GUID_NULL si no se especifica el tipo de objeto en la ACE, o si la ACE no es una ACE del objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado. Esto se establecerá en GUID_NULL si no se especifica el tipo de objeto heredado de la ACE, o si la ACE no es una ACE del objeto.

### <a name="remarks"></a>Comentarios

Este método recupera toda la información sobre una ACE individual, que proporciona más información que [CAcl::GetAclEntries](#getaclentries) por sí solo hace que estén disponibles.

Consulte [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) para obtener más detalles sobre los tipos ACE y marcas.

##  <a name="getlength"></a>  CAcl::GetLength

Devuelve la longitud de la lista de control de acceso (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud requerida en bytes es necesario para retener el `ACL` estructura.

##  <a name="getpacl"></a>  CAcl::GetPACL

Devuelve un puntero a una lista de control de acceso (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `ACL` estructura.

##  <a name="isempty"></a>  CAcl::IsEmpty

Las pruebas del `CAcl` objeto para las entradas.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve TRUE si el `CAcl` objeto no es NULL y no contiene ninguna entrada. Devuelve FALSE si el `CAcl` objeto es NULL o contiene al menos una entrada.

##  <a name="isnull"></a>  CAcl::IsNull

Devuelve el estado de la `CAcl` objeto.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el `CAcl` objeto es NULL, FALSE en caso contrario.

##  <a name="operator_const_acl__star"></a>  ACL de CAcl::operator const *

Convierte un `CAcl` objeto a un `ACL` estructura (lista de control de acceso).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Devuelve la dirección de la `ACL` estructura.

##  <a name="operator_eq"></a>  CAcl::operator =

Operador de asignación.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*RHS*<br/>
El `CAcl` para asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la actualización `CAcl` objeto.

##  <a name="removeace"></a>  CAcl::RemoveAce

Quita una ACE específica (entrada de control de acceso) de la `CAcl` objeto.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la entrada ACE para quitar.

### <a name="remarks"></a>Comentarios

Este método se deriva [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>  CAcl::RemoveAces

Quita alls entradas de control de acceso de la `CAcl` que se aplican a la determinada `CSid`.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Referencia a un objeto `CSid`.

##  <a name="setempty"></a>  CAcl::SetEmpty

Las marcas de la `CAcl` objeto como vacío.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Comentarios

El `CAcl` puede establecerse en vacío o en NULL: los dos estados son distintos.

##  <a name="setnull"></a>  CAcl::SetNull

Las marcas de la `CAcl` objeto como NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Comentarios

El `CAcl` puede establecerse en vacío o en NULL: los dos estados son distintos.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
