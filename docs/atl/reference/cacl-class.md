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
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497889"
---
# <a name="cacl-class"></a>Clase CAcl

Esta clase es un contenedor para una `ACL` estructura (lista de control de acceso).

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAcl
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Matriz de ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Matriz de BYTEs.|
|[CAcl::CAceTypeArray](#cacetypearray)|Matriz de BYTEs.|

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|El constructor.|
|[CAcl::~CAcl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Devuelve el número de objetos de entrada de control de acceso (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Recupera las entradas de la `CAcl` lista de control de acceso (ACL) del objeto.|
|[CAcl::GetAclEntry](#getaclentry)|Recupera toda la información sobre una entrada en un `CAcl` objeto.|
|[CAcl::GetLength](#getlength)|Devuelve la longitud de la ACL.|
|[CAcl::GetPACL](#getpacl)|Devuelve un paquetes (puntero a una ACL).|
|[CAcl::IsEmpty](#isempty)|Prueba el `CAcl` objeto para las entradas.|
|[CAcl::IsNull](#isnull)|Devuelve el estado del `CAcl` objeto.|
|[CAcl::RemoveAce](#removeace)|Quita una ACE específica (entrada de control de acceso) del `CAcl` objeto.|
|[CAcl::RemoveAces](#removeaces)|Quita todas las ACE (entradas de control de acceso) `CAcl` del que se aplican `CSid`a la determinada.|
|[CAcl::SetEmpty](#setempty)|Marca el `CAcl` objeto como vacío.|
|[CAcl::SetNull](#setnull)|Marca el `CAcl` objeto como null.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAcl:: Operator const ACL *](#operator_const_acl__star)|Convierte un `CAcl` objeto en una `ACL` estructura.|
|[CAcl:: Operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

La `ACL` estructura es el encabezado de una ACL (lista de control de acceso). Una ACL incluye una lista secuencial de cero o más [ACE](/windows/win32/SecAuthZ/access-control-entries) (entradas de control de acceso). Las ACE individuales de una ACL se numeran de 0 a *n-1*, donde *n* es el número de ACE de la ACL. Al editar una ACL, una aplicación hace referencia a una entrada de control de acceso (ACE) dentro de la ACL por su índice.

Hay dos tipos de ACL:

- Discrecional

- Sistema

Un ACL discrecional se controla mediante el propietario de un objeto o cualquier persona que haya concedido el acceso a WRITE_DAC al objeto. Especifica que los usuarios y grupos específicos de Access pueden tener un objeto. Por ejemplo, el propietario de un archivo puede utilizar una ACL discrecional para controlar qué usuarios y grupos pueden y no pueden tener acceso al archivo.

Un objeto también puede tener asociada información de seguridad de nivel de sistema, en forma de una ACL del sistema controlada por un administrador del sistema. Una ACL del sistema puede permitir al administrador del sistema auditar cualquier intento de obtener acceso a un objeto.

Para obtener más información, consulte la explicación de la [ACL](/windows/win32/SecAuthZ/access-control-lists) en el Windows SDK.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

##  <a name="caccessmaskarray"></a>  CAcl::CAccessMaskArray

Matriz de objetos ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Comentarios

Este typedef especifica el tipo de matriz que se puede usar para almacenar derechos de acceso utilizados en entradas de control de acceso (ACE).

##  <a name="caceflagarray"></a>  CAcl::CAceFlagArray

Matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Comentarios

Este typedef especifica el tipo de matriz que se usa para definir las marcas de control específicas del tipo de entrada de control de acceso (ACE). Consulte la definición de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para ver la lista completa de posibles marcas.

##  <a name="cacetypearray"></a>  CAcl::CAceTypeArray

Matriz de BYTEs.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Comentarios

Este typedef especifica el tipo de matriz que se usa para definir la naturaleza de los objetos de entrada de control de acceso (ACE), como ACCESS_ALLOWED_ACE_TYPE o ACCESS_DENIED_ACE_TYPE. Vea la definición de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener una lista completa de los tipos posibles.

##  <a name="cacl"></a>  CAcl::CAcl

El constructor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
Objeto `CAcl` existente.

### <a name="remarks"></a>Comentarios

El `CAcl` objeto se puede crear opcionalmente con un objeto `CAcl` existente.

##  <a name="dtor"></a>  CAcl::~CAcl

Destructor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera todos los recursos adquiridos por el objeto.

##  <a name="getacecount"></a>  CAcl::GetAceCount

Devuelve el número de objetos de entrada de control de acceso (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de entradas ACE en el `CAcl` objeto.

##  <a name="getaclentries"></a>CAcl::GetAclEntries

Recupera las entradas de la `CAcl` lista de control de acceso (ACL) del objeto.

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

### <a name="remarks"></a>Comentarios

Este método rellena los parámetros de la matriz con los detalles de todos los objetos ACE contenidos `CAcl` en el objeto. Use NULL cuando no se requieran los detalles de esa matriz en particular.

El contenido de cada matriz se corresponde entre el otro, es decir, el primer elemento de `CAccessMaskArray` la matriz corresponde al primer elemento de la `CSidArray` matriz, y así sucesivamente.

Vea [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener más información sobre los tipos de ACE y las marcas.

##  <a name="getaclentry"></a>  CAcl::GetAclEntry

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
Tipo del objeto. Se establecerá en GUID_NULL si el tipo de objeto no se especifica en la ACE, o si la ACE no es una ACE de objeto.

*pInheritedObjectType*<br/>
El tipo de objeto heredado. Se establecerá en GUID_NULL si el tipo de objeto heredado no se especifica en la ACE, o si la ACE no es una ACE de objeto.

### <a name="remarks"></a>Comentarios

Este método recuperará toda la información sobre una ACE individual, lo que proporciona más información de la que [CAcl:: GetAclEntries](#getaclentries) solo pone a su disposición.

Vea [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) para obtener más información sobre los tipos de ACE y las marcas.

##  <a name="getlength"></a>  CAcl::GetLength

Devuelve la longitud de la lista de control de acceso (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud necesaria en bytes necesaria para contener la `ACL` estructura.

##  <a name="getpacl"></a>  CAcl::GetPACL

Devuelve un puntero a una lista de control de acceso (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `ACL` estructura.

##  <a name="isempty"></a>CAcl:: IsEmpty

Prueba el `CAcl` objeto para las entradas.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve true si el `CAcl` objeto no es NULL y no contiene ninguna entrada. Devuelve false si el `CAcl` objeto es null o contiene al menos una entrada.

##  <a name="isnull"></a>  CAcl::IsNull

Devuelve el estado del `CAcl` objeto.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el `CAcl` objeto es null, de lo contrario, false.

##  <a name="operator_const_acl__star"></a>CAcl:: Operator const ACL *

Convierte un `CAcl` objeto en una `ACL` estructura (lista de control de acceso).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Comentarios

Devuelve la dirección de la `ACL` estructura.

##  <a name="operator_eq"></a>CAcl:: Operator =

Operador de asignación.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parámetros

*rhs*<br/>
`CAcl` Que se va a asignar al objeto existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto actualizado `CAcl` .

##  <a name="removeace"></a>  CAcl::RemoveAce

Quita una ACE específica (entrada de control de acceso) del `CAcl` objeto.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la entrada ACE que se va a quitar.

### <a name="remarks"></a>Comentarios

Este método se deriva de [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>CAcl::RemoveAces

Quita las ACE de Alls (entradas de control de acceso `CAcl` ) del que se aplican a la determinada. `CSid`

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Referencia a un objeto `CSid`.

##  <a name="setempty"></a>CAcl::SetEmpty

Marca el `CAcl` objeto como vacío.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Comentarios

Se `CAcl` puede establecer en Empty o en NULL: los dos Estados son distintos.

##  <a name="setnull"></a>  CAcl::SetNull

Marca el `CAcl` objeto como null.

```
void SetNull() throw();
```

### <a name="remarks"></a>Comentarios

Se `CAcl` puede establecer en Empty o en NULL: los dos Estados son distintos.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Funciones globales de seguridad](../../atl/reference/security-global-functions.md)
