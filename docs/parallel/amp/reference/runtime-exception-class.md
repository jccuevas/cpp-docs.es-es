---
title: runtime_exception (clase)
ms.date: 03/27/2019
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: ff54357055d373db98f469b071edc75fce75e0b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336795"
---
# <a name="runtime_exception-class"></a>runtime_exception (clase)

El tipo base para las excepciones en la biblioteca de C++ Paralelismo Masivo Acelerado (AMP).

### <a name="syntax"></a>Sintaxis

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor runtime_exception](#ctor)|Inicializa una nueva instancia de la clase `runtime_exception`.|
|[Destructor de runtime_exception](#dtor)|Destruye el objeto `runtime_exception`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_error_code](#get_error_code)|Devuelve el código de error que provocó la excepción.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operador](#operator_eq)|Copia el contenido del `runtime_exception` objeto especificado en éste.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres:** Concurrencia

## <a name="runtime_exception-constructor"></a><a name="ctor"></a>Constructor runtime_exception

Inicializa una nueva instancia de la clase.

### <a name="syntax"></a>Sintaxis

```cpp
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Una descripción del error que causó la excepción.

*_Hresult*<br/>
El HRESULT del error que causó la excepción.

*_Other*<br/>
El objeto `runtime_exception` que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Objeto `runtime_exception`.

## <a name="runtime_exception-destructor"></a><a name="dtor"></a>Destructor de runtime_exception

Destruye el objeto.

### <a name="syntax"></a>Sintaxis

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a><a name="get_error_code"></a>get_error_code

Devuelve el código de error que provocó la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valor devuelto

El HRESULT del error que causó la excepción.

## <a name="operator"></a><a name="operator_eq"></a>operador

Copia el contenido del `runtime_exception` objeto especificado en éste.

### <a name="syntax"></a>Sintaxis

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El objeto `runtime_exception` que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Una referencia `runtime_exception` a este objeto.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
