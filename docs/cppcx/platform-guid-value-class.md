---
title: Platform::Guid (Clase de valor)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 0a339de3aec14b6bd1dc461f53c1a7417db738ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482932"
---
# <a name="platformguid-value-class"></a>Platform::Guid (Clase de valor)

Representa un tipo [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) en el sistema de tipos de Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
public value struct Guid
```

### <a name="members"></a>Miembros

Guid tiene los métodos Equals(), GetHashCode() y ToString() que se derivan de [Platform::Object Class](../cppcx/platform-object-class.md), y el método GetTypeCode() que se deriva de [Platform::Type Class](../cppcx/platform-type-class.md). Guid también tiene los siguientes miembros.

|Miembro|Descripción|
|------------|-----------------|
|[Guid](#ctor)|Inicializa una nueva instancia del struct Guid.|
|[operator==](#operator-equality)|Operador Equals (de igualdad).|
|[operator!=](#operator-not-equal)|Operador Not Equals (de desigualdad).|
|[operator()](#operator-call)|Convierte un Guid en un GUID.|

### <a name="remarks"></a>Comentarios

Para obtener un ejemplo sobre cómo generar un nuevo elemento Platform::Guid mediante el uso de la función de Windows [CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid), consulte [WinRT component: How to generate a GUID?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)(Componente de WinRT: ¿Cómo generar un GUID?).

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd

## <a name="ctor"></a> Constructores de GUID

Inicializa una nueva instancia de un struct Guid.

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
Los cuatro primeros bytes del identificador exclusivo global (GUID).

*b*<br/>
Los dos bytes siguientes del identificador exclusivo global (GUID).

*c*<br/>
Los dos bytes siguientes del identificador exclusivo global (GUID).

*d*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*e*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*f*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*g*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*h*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*i*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*J*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*k*<br/>
El byte siguiente del identificador exclusivo global (GUID).

*m*<br/>
Un GUID, tal como se define.

*n*<br/>
Los ocho bytes restantes del identificador exclusivo global (GUID).

## <a name="operator-equality"></a> GUID::operator == (operador)

Compara dos GUID.

### <a name="syntax"></a>Sintaxis

```cpp
Platform::Guid::operator==
```

### <a name="return-value"></a>Valor devuelto

True si los dos GUID son iguales.

## <a name="operator-inequality"></a> GUID::operator! = (operador)

Compara dos GUID.

### <a name="syntax"></a>Sintaxis

```cpp
Platform::Guid::operator!=
```

### <a name="return-value"></a>Valor devuelto

True si los dos GUID no son iguales.

## <a name="operator-call"></a> ::Operator() (operador)

Convierte implícitamente un [estructura GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931)GUID en Platform::.

### <a name="syntax"></a>Sintaxis

```cpp
Platform::Guid operator();
```

### <a name="return-value"></a>Valor devuelto

Un struct de Guid.

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)