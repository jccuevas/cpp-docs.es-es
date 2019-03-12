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
ms.openlocfilehash: 7b6ab42dc630ce7e0014534064e8f1ce6da00857
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750928"
---
# <a name="platformstringreference-class"></a>Platform::StringReference (Clase)

Tipo de optimización que puedes usar para pasar datos de tipo String desde parámetros de entrada `Platform::String^` a otros métodos con un mínimo de operaciones de copia.

## <a name="syntax"></a>Sintaxis

```cpp
class StringReference
```

### <a name="remarks"></a>Comentarios

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|Dos constructores para crear instancias de `StringReference`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[StringReference::Data](#data)|Devuelve los datos de tipo String como una matriz de valores char16.|
|[StringReference::Length](#length)|Devuelve el número de caracteres de la cadena.|
|[StringReference::GetHSTRING](#gethstring)|Devuelve los datos de tipo String como HSTRING.|
|[StringReference::GetString](#getstring)|Devuelve los datos de tipo String como `Platform::String^`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[StringReference::operator=](#operator-assign)|Asigna `StringReference` a una nueva instancia de `StringReference` .|
|[StringReference::operator()](#operator-call)|Convierte `StringReference` en `Platform::String^`.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Encabezado:** vccorlib.h

## <a name="data"></a>  Stringreference (método)

Devuelve el contenido de este `StringReference` como matriz de valores char16.

### <a name="syntax"></a>Sintaxis

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>Valor devuelto

Matriz de caracteres de texto UNICODE char16.

## <a name="gethstring"></a>  Gethstring (método)

Devuelve el contenido de la cadena como `__abi_HSTRING`.

### <a name="syntax"></a>Sintaxis

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>Valor devuelto


  `__abi_HSTRING` que contiene los datos de tipo String.

### <a name="remarks"></a>Comentarios

## <a name="getstring"></a>  Stringreference (método)

Devuelve el contenido de la cadena como `Platform::String^`.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>Valor devuelto

`Platform::String^` que contiene los datos de tipo String.

## <a name="length"></a>  Stringreference (método)

Devuelve el número de caracteres de la cadena.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>Valor devuelto

Un entero sin signo que especifica la cantidad de caracteres de la cadena.

### <a name="remarks"></a>Comentarios

## <a name="operator-assign"></a>  StringReference::operator= Operator

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

### <a name="remarks"></a>Comentarios

Dado que `StringReference` es una clase de C++ estándar y no una clase ref, no aparece en el **Examinador de objetos**.

## <a name="operator-call"></a>  StringReference::operator()  Operator

Convierte un objeto `StringReference` en un objeto `Platform::String^`.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador para un objeto de tipo `Platform::String`.

## <a name="ctor"></a>  StringReference::StringReference (Constructor)

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

### <a name="remarks"></a>Comentarios

La primera versión de este constructor es el constructor predeterminado. La segunda versión inicializa una nueva clase de instancia `StringReference` desde el objeto especificado por el parámetro `__fstrArg`. La tercera y la cuarta sobrecargas inicializan una nueva instancia de `StringReference` desde una matriz de valores char16. char16 representa un carácter de texto UNICODE de 16 bits.

## <a name="see-also"></a>Vea también

[Platform::StringReference (Clase)](../cppcx/platform-stringreference-class.md)
