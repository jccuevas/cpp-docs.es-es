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
ms.openlocfilehash: 6ad784720833d2ae5de7d653d132ba144aec2677
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126387"
---
# <a name="runtime_exception-class"></a>runtime_exception (clase)

El tipo base para las excepciones en C++ la biblioteca de paralelismo masivo acelerado (amp).

### <a name="syntax"></a>Sintaxis

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de runtime_exception](#ctor)|Inicializa una nueva instancia de la clase `runtime_exception`.|
|[~ runtime_exception destructor](#dtor)|Destruye el objeto `runtime_exception`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_error_code](#get_error_code)|Devuelve el código de error que produjo la excepción.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Copia el contenido del objeto `runtime_exception` especificado en este.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** Concurrency

## <a name="ctor"></a>Constructor de runtime_exception

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
Descripción del error que produjo la excepción.

*_Hresult*<br/>
HRESULT de error que produjo la excepción.

*_Other*<br/>
El objeto `runtime_exception` que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Objeto `runtime_exception`.

## <a name="dtor"></a>~ runtime_exception destructor

Destruye el objeto.

### <a name="syntax"></a>Sintaxis

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a>get_error_code

Devuelve el código de error que produjo la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT de error que produjo la excepción.

## <a name="operator_eq"></a>  operator=
  Copia el contenido del objeto `runtime_exception` especificado en este.

### <a name="syntax"></a>Sintaxis

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El objeto `runtime_exception` que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `runtime_exception`.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
