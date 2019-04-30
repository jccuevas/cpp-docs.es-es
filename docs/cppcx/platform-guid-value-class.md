---
title: Platform::Guid (Clase de valor)
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 64c70b619380d7c2ed4aaaecad3ee01a1d0f79c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383326"
---
# <a name="platformguid-value-class"></a>Platform::Guid (Clase de valor)

Representa un tipo [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) en el sistema de tipos de Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
public value struct Guid
```

### <a name="members"></a>Miembros

`Platform::Guid` tiene la `Equals()`, `GetHashCode()`, y `ToString()` derivan de métodos el [Platform:: Object Class](../cppcx/platform-object-class.md)y el `GetTypeCode()` método deriva el [Platform:: Type Class](../cppcx/platform-type-class.md). `Platform::Guid` También tiene los siguientes miembros.

|Miembro|Descripción|
|------------|-----------------|
|[Guid](#ctor)|Inicializa una nueva instancia de `Platform::Guid`.|
|[operator==](#operator-equality)|Operador Equals (de igualdad).|
|[operator!=](#operator-inequality)|Operador Not Equals (de desigualdad).|
|[operator&lt;](#operator-less)|Operador menor que.|
|[operator()](#operator-call)|Convierte `Platform::Guid` en `GUID`.|

### <a name="remarks"></a>Comentarios

Para generar un nuevo `Platform::Guid`, utilice el [Windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) método estático.

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="ctor"></a> Constructores de GUID

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
Los primeros 4 bytes de la `GUID`.

*b*<br/>
Los 2 bytes de la `GUID`.

*c*<br/>
Los 2 bytes de la `GUID`.

*d*<br/>
El siguiente byte de la `GUID`.

*e*<br/>
El siguiente byte de la `GUID`.

*f*<br/>
El siguiente byte de la `GUID`.

*g*<br/>
El siguiente byte de la `GUID`.

*h*<br/>
El siguiente byte de la `GUID`.

*i*<br/>
El siguiente byte de la `GUID`.

*j*<br/>
El siguiente byte de la `GUID`.

*k*<br/>
El siguiente byte de la `GUID`.

*m*<br/>
Un `GUID` en forma un [estructura GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931).

*n*<br/>
Los 8 bytes restantes de la `GUID`.

## <a name="operator-equality"></a> GUID::operator == (operador)

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

True si los dos `Platform::Guid` instancias son iguales.

### <a name="remarks"></a>Comentarios

Prefieren usar la `==` en lugar del operador los [Windows::Foundation::GuidHelper::Equals](/uwp/api/windows.foundation.guidhelper.equals) método estático.

## <a name="operator-inequality"></a> GUID::operator! = (operador)

Compara dos `Platform::Guid` instancias no son iguales.

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

True si los dos `Platform::Guid` instancias no son iguales.

## <a name="operator-less"></a> GUID::operator&lt; operador

Compara dos `Platform::Guid` instancias para la ordenación.

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

True si *guid1* está ordenado antes *guid2*. La ordenación es lexicográfica después de tratar cada `Platform::Guid` como si fuera una matriz de cuatro valores sin signo de 32 bits. Esto no es el orden utilizado por SQL Server o .NET Framework, ni es el mismo que el orden lexicográfico con representación de cadena.

Este operador se proporciona para que `Guid` la biblioteca estándar de C++ pueden consumir más fácilmente los objetos.

## <a name="operator-call"></a> ::Operator() (operador)

Convierte implícitamente un `Platform::Guid` a un [estructura GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931).

### <a name="syntax"></a>Sintaxis

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Valor devuelto

Un [estructura GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931).

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
