---
title: Platform::Guid (Clase de valor)
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: f63b2bb4fd5f809861622a4f6b255ee3725564b6
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816591"
---
# <a name="platformguid-value-class"></a>Platform::Guid (Clase de valor)

Representa un tipo [GUID](/previous-versions/cc317743(v%3dmsdn.10)) en el sistema de tipos de Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
public value struct Guid
```

### <a name="members"></a>Miembros

`Platform::Guid` tiene los métodos `Equals()`, `GetHashCode()`y `ToString()` derivados de la [clase Platform:: Object](../cppcx/platform-object-class.md)y el método `GetTypeCode()` derivado de la [clase Platform:: Type](../cppcx/platform-type-class.md). `Platform::Guid` también tiene los siguientes miembros.

|Miembro|Descripción|
|------------|-----------------|
|[GUID](#ctor)|Inicializa una nueva instancia de `Platform::Guid`.|
|[operator==](#operator-equality)|Operador de igualdad.|
|[operator!=](#operator-inequality)|Operador de desigualdad.|
|[operator&lt;](#operator-less)|Operador menor que.|
|[operator()](#operator-call)|Convierte `Platform::Guid` en `GUID`.|

### <a name="remarks"></a>Comentarios

Para generar una nueva `Platform::Guid`, use el método estático [Windows:: Foundation:: GuidHelper:: CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) .

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd

## <a name="ctor"></a>GUID:: GUID (constructores)

Inicializa una nueva instancia de `Platform::Guid`.

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

*a*<br/>
Los primeros 4 bytes del `GUID`.

*b*<br/>
Los 2 bytes siguientes del `GUID`.

*c*<br/>
Los 2 bytes siguientes del `GUID`.

*d*<br/>
Siguiente byte del `GUID`.

*e*<br/>
Siguiente byte del `GUID`.

*f*<br/>
Siguiente byte del `GUID`.

*g*<br/>
Siguiente byte del `GUID`.

*h*<br/>
Siguiente byte del `GUID`.

*i*<br/>
Siguiente byte del `GUID`.

*j*<br/>
Siguiente byte del `GUID`.

*k*<br/>
Siguiente byte del `GUID`.

*m*<br/>
Un `GUID` en la forma de una [estructura GUID](/previous-versions/cc317743(v%3dmsdn.10)).

*n*<br/>
Los 8 bytes restantes del `GUID`.

## <a name="operator-equality"></a>GUID:: Operator = = (operador)

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

True si las dos instancias de `Platform::Guid` son iguales.

### <a name="remarks"></a>Comentarios

Prefiere usar el operador `==` en lugar del método estático [Windows:: Foundation:: GuidHelper:: Equals](/uwp/api/windows.foundation.guidhelper.equals) .

## <a name="operator-inequality"></a>GUID:: Operator! = (operador)

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

True si las dos instancias de `Platform::Guid` no son iguales.

## <a name="operator-less"></a>GUID:: Operator&lt; (operador)

Compara dos instancias de `Platform::Guid` para su ordenación.

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

True si *guid1* está ordenado antes de *GUID2*. La ordenación es lexicográfico después de tratar cada `Platform::Guid` como si fuese una matriz de valores sin signo de 4 32 bits. No es el orden utilizado por SQL Server o el .NET Framework, ni tampoco lo mismo que la ordenación de lexicográfica por representación de cadena.

Este operador se proporciona para que la C++ biblioteca estándar pueda usar más fácilmente `Guid` objetos.

## <a name="operator-call"></a>GUID:: Operator () (operador)

Convierte implícitamente un `Platform::Guid` en una [estructura GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="syntax"></a>Sintaxis

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Valor devuelto

[Estructura GUID](/previous-versions/cc317743(v%3dmsdn.10)).

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
