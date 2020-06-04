---
title: Platform::IntPtr (Clase de valor)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
ms.openlocfilehash: 8101fa2c82a0ac3e3b573384d14d9a7eff6ecf61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152744"
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr (Clase de valor)

Representa un puntero o un identificador con signo cuyo tamaño es específico de la plataforma (32 bits o 64 bits).

## <a name="syntax"></a>Sintaxis

```cpp
public value struct IntPtr
```

### <a name="members"></a>Miembros

IntPtr tiene los siguientes miembros:

|Miembro|Descripción|
|------------|-----------------|
|[IntPtr::IntPtr](#ctor)|Inicializa una nueva instancia de IntPtr.|
|[IntPtr::op_explicit (Operador)](#op-explicit)|Convierte el parámetro especificado un IntPtr o un puntero a un valor de IntPtr.|
|[IntPtr::ToInt32](#toint32)|Convierte el IntPtr actual en un entero de 32 bits.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="ctor"> </a> IntPtr::IntPtr (Constructor)

Inicializa una nueva instancia de un objeto IntPtr con el valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Un identificador o un puntero de 64 bits, o un puntero a un valor de 64 bits, o un valor de 32 bits que se puede convertir en un valor de 64 bits.

## <a name="op-explicit"> </a> IntPtr::op_explicit (Operador)

Convierte el parámetro especificado un IntPtr o un puntero a un valor de IntPtr.

### <a name="syntax"></a>Sintaxis

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>Parámetros

*value1*<br/>
Un puntero a un identificador o IntPtr.

*value2*<br/>
Un entero de 32 bits que se puede convertir en un objeto IntPtr.

*value3*<br/>
Un objeto IntPtr.

### <a name="return-value"></a>Valor devuelto

Los operadores primero y segundo devuelven un objeto IntPtr. El tercer operador devuelve un puntero al valor representado por el objeto IntPtr actual.

## <a name="toint32"> </a> Toint32 (método)

Convierte el valor IntPtr actual en un entero de 32 bits.

### <a name="syntax"></a>Sintaxis

```cpp
int32 IntPtr::ToInt32();
```

### <a name="return-value"></a>Valor devuelto

Un entero de 32 bits.

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
