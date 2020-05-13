---
title: Platform::StringReference (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 4748eecdf67ae5a60ddf97783a934a05e80b406c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374661"
---
# <a name="platformstringreference-class"></a>Platform::StringReference (Clase)

Tipo de optimización que puedes usar para pasar datos de tipo String desde parámetros de entrada `Platform::String^` a otros métodos con un mínimo de operaciones de copia.

## <a name="syntax"></a>Sintaxis

```cpp
class StringReference
```

### <a name="remarks"></a>Observaciones

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|Dos constructores para crear instancias de `StringReference`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[StringReference::Data](#data)|Devuelve los datos de tipo String como una matriz de valores char16.|
|[StringReference::Longitud](#length)|Devuelve el número de caracteres de la cadena.|
|[StringReference::GetHSTRING](#gethstring)|Devuelve los datos de tipo String como HSTRING.|
|[StringReference::GetString](#getstring)|Devuelve los datos de tipo String como `Platform::String^`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[StringReference::operator ?](#operator-assign)|Asigna `StringReference` a una nueva instancia de `StringReference` .|
|[StringReference::operator()](#operator-call)|Convierte `StringReference` en `Platform::String^`.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Encabezado:** vccorlib.h

## <a name="stringreferencedata-method"></a><a name="data"></a>StringReference::Data Método

Devuelve el contenido de este `StringReference` como matriz de valores char16.

### <a name="syntax"></a>Sintaxis

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>Valor devuelto

Matriz de caracteres de texto UNICODE char16.

## <a name="stringreferencegethstring-method"></a><a name="gethstring"></a>StringReference::GetHSTRING Método

Devuelve el contenido de la cadena como `__abi_HSTRING`.

### <a name="syntax"></a>Sintaxis

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>Valor devuelto

`__abi_HSTRING` que contiene los datos de tipo String.

### <a name="remarks"></a>Observaciones

## <a name="stringreferencegetstring-method"></a><a name="getstring"></a>StringReference::GetString Método

Devuelve el contenido de la cadena como `Platform::String^`.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>Valor devuelto

`Platform::String^` que contiene los datos de tipo String.

## <a name="stringreferencelength-method"></a><a name="length"></a>StringReference::Método Length

Devuelve el número de caracteres de la cadena.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>Valor devuelto

Un entero sin signo que especifica la cantidad de caracteres de la cadena.

### <a name="remarks"></a>Observaciones

## <a name="stringreferenceoperator-operator"></a><a name="operator-assign"></a>StringReference::operator- Operador

Asigna el objeto especificado al objeto `StringReference` actual.

### <a name="syntax"></a>Sintaxis

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>Parámetros

*__fstrArg*<br/>
Dirección de un objeto `StringReference` que se usa para inicializar el objeto `StringReference` actual.

*__strArg*<br/>
Puntero a una matriz de valores char16 que se usa para inicializar el objeto `StringReference` actual.

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto de tipo `StringReference`.

### <a name="remarks"></a>Observaciones

Dado `StringReference` que es una clase C++ estándar y no una clase ref, no aparece en el **Examinador de objetos**.

## <a name="stringreferenceoperator--operator"></a><a name="operator-call"></a>StringReference::operator() Operador

Convierte un objeto `StringReference` en un objeto `Platform::String^`.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador para un objeto de tipo `Platform::String`.

## <a name="stringreferencestringreference-constructor"></a><a name="ctor"></a>StringReference::StringReference Constructor

Inicializa una nueva instancia de la clase `StringReference`.

### <a name="syntax"></a>Sintaxis

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>Parámetros

*__fstrArg*<br/>
`StringReference` cuyos datos se usan para inicializar la nueva instancia.

*__strArg*<br/>
Puntero a una matriz de valores char16 que se emplea para inicializar la nueva instancia.

*__lenArg*<br/>
Número de elementos de `__strArg`.

### <a name="remarks"></a>Observaciones

La primera versión de este constructor es el constructor predeterminado. La segunda versión inicializa una nueva clase de instancia `StringReference` desde el objeto especificado por el parámetro `__fstrArg`. La tercera y la cuarta sobrecargas inicializan una nueva instancia de `StringReference` desde una matriz de valores char16. char16 representa un carácter de texto UNICODE de 16 bits.

## <a name="see-also"></a>Consulte también

[Platform::StringReference (Clase)](../cppcx/platform-stringreference-class.md)
