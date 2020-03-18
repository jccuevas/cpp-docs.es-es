---
title: nested_exception (clase)
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: ed58eb6cc074b54ae6801d2b11089af9a79f8c8f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441620"
---
# <a name="nested_exception-class"></a>nested_exception (clase)

La clase describe una excepción para su uso con herencia múltiple. Captura la excepción administrada actualmente y la almacena para su uso posterior.

## <a name="syntax"></a>Sintaxis

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>Members

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>Functions

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Produce la excepción almacenada.|
|[nested_ptr](#nested_ptr)|Devuelve la excepción almacenada.|

### <a name="op_as"></a>operador =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Valor devuelto

Excepción almacenada capturada por este objeto `nested_exception`.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Observaciones

Si `nested_ptr()` devuelve un puntero nulo, la función llama a `std::terminate()`. De lo contrario, produce la excepción almacenada capturada por `*this`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<excepción >

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

\ de [clase de excepción](../standard-library/exception-class.md)
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
