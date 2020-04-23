---
title: Platform::Guid (Clase de valor)
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 3849074f93424912b1dc5b93883482a6cb55892a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750656"
---
# <a name="platformguid-value-class"></a>Platform::Guid (Clase de valor)

Representa un tipo [GUID](/windows/win32/api/guiddef/ns-guiddef-guid en el sistema de tipos de Windows runtime.

## <a name="syntax"></a>Sintaxis

```cpp
public value struct Guid
```

### <a name="members"></a>Miembros

`Platform::Guid`tiene `Equals()`los `GetHashCode()`métodos , , `ToString()` y derivados de `GetTypeCode()` la clase [Platform::Object](../cppcx/platform-object-class.md)y el método derivado de la clase [Platform::Type](../cppcx/platform-type-class.md). `Platform::Guid`también tiene los siguientes miembros.

|Member|Descripción|
|------------|-----------------|
|[Guid](#ctor)|Inicializa una nueva instancia de un `Platform::Guid`.|
|[operadora](#operator-equality)|Operador igual a.|
|[¡Operador!](#operator-inequality)|Operador distinto de.|
|[Operador&lt;](#operator-less)|Operador menor que.|
|[operador()](#operator-call)|Convierte `Platform::Guid` en `GUID`.|

### <a name="remarks"></a>Observaciones

Para generar `Platform::Guid`un nuevo , utilice el método estático [Windows::Foundation::GuidHelper::CreateNewGuid.](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid)

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Metadatos:** platform.winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a>Guid::Guid Constructores

Inicializa una nueva instancia de un `Platform::Guid`.

### <a name="syntax"></a>Sintaxis

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>Parámetros

*Un*<br/>
Los primeros 4 `GUID`bytes del archivo .

*B*<br/>
Los 2 bytes `GUID`siguientes del archivo .

*C*<br/>
Los 2 bytes `GUID`siguientes del archivo .

*D*<br/>
El siguiente byte de `GUID`.

*e*<br/>
El siguiente byte de `GUID`.

*F*<br/>
El siguiente byte de `GUID`.

*G*<br/>
El siguiente byte de `GUID`.

*H*<br/>
El siguiente byte de `GUID`.

*Ⅰ*<br/>
El siguiente byte de `GUID`.

*J*<br/>
El siguiente byte de `GUID`.

*K*<br/>
El siguiente byte de `GUID`.

*M*<br/>
A `GUID` en el formulario una [estructura GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

*n*<br/>
Los 8 bytes restantes del `GUID`archivo .

## <a name="guidoperator-operator"></a><a name="operator-equality"></a>Guid::operador - Operador

Compara dos instancias de `Platform::Guid` para determinar si sus valores son iguales.

### <a name="syntax"></a>Sintaxis

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parámetros

*guid1*<br/>
Primer objeto `Platform::Guid` que se va a comparar.

*guid2*<br/>
Segundo objeto `Platform::Guid` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

True si `Platform::Guid` las dos instancias son iguales.

### <a name="remarks"></a>Observaciones

Prefiere usar `==` el operador en lugar de la [Windows::Foundation::GuidHelper::Equals](/uwp/api/windows.foundation.guidhelper.equals) método estático.

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a>Guid::operator!

Compara dos instancias de `Platform::Guid` para determinar si no son iguales.

### <a name="syntax"></a>Sintaxis

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parámetros

*guid1*<br/>
Primer objeto `Platform::Guid` que se va a comparar.

*guid2*<br/>
Segundo objeto `Platform::Guid` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

True si `Platform::Guid` las dos instancias no son iguales.

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a>Guid::operador&lt; Operador

Compara dos `Platform::Guid` instancias para realizar pedidos.

### <a name="syntax"></a>Sintaxis

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parámetros

*guid1*<br/>
Primer objeto `Platform::Guid` que se va a comparar.

*guid2*<br/>
Segundo objeto `Platform::Guid` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

True si *guid1* se ordena antes *de guid2*. El orden es lexicográfico `Platform::Guid` después de tratar cada uno como si fuera una matriz de cuatro valores sin signo de 32 bits. Este no es el orden utilizado por SQL ServerSQL Server o .NET Framework, ni es lo mismo que el orden lexicográfico por representación de cadena.

Este operador se `Guid` proporciona para que los objetos puedan ser consumidos más fácilmente por la biblioteca estándar C++.

## <a name="guidoperator-operator"></a><a name="operator-call"></a>Guid::operator() Operador

Convierte implícitamente `Platform::Guid` a en una [estructura GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

### <a name="syntax"></a>Sintaxis

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Valor devuelto

Una [estructura GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
