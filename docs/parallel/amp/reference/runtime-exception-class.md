---
title: runtime_exception (clase)
ms.date: 11/04/2016
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: 627fc6788dd359779bf07da3da1901be4c3aeafd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630690"
---
# <a name="runtimeexception-class"></a>runtime_exception (clase)

El tipo base para las excepciones en la biblioteca de C++ Accelerated masivos Parallelism (AMP).

### <a name="syntax"></a>Sintaxis

```
class runtime_exception : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[runtime_exception (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `runtime_exception`.|
|[~ runtime_exception (destructor)](#dtor)|Destruye el objeto `runtime_exception`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_error_code](#runtime_exception__get_error_code)|Devuelve el código de error que provocó la excepción.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `runtime_exception` objeto en este.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres:** Concurrency

## <a name="runtime_exception__ctor"></a>  runtime_exception (Constructor)

Inicializa una nueva instancia de la clase.

### <a name="syntax"></a>Sintaxis

```
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Una descripción del error que provocó la excepción.

*_Hresult*<br/>
El valor HRESULT de error que provocó la excepción.

*_Otro*<br/>
La `runtime_exception` objeto que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Objeto `runtime_exception`.

## <a name="dtor"></a>  ~ runtime_exception (destructor)

Destruye el objeto.

### <a name="syntax"></a>Sintaxis

```
virtual ~runtime_exception() throw();
```

## <a name="runtime_exception__get_error_code"></a>  get_error_code

Devuelve el código de error que provocó la excepción.

### <a name="syntax"></a>Sintaxis

```
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Valor devuelto

El valor HRESULT de error que provocó la excepción.

## <a name="runtime_exception__operator_eq"></a>  operator=
  Copia el contenido del elemento especificado `runtime_exception` objeto en este.

### <a name="syntax"></a>Sintaxis

```
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `runtime_exception` objeto que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `runtime_exception` objeto.

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
