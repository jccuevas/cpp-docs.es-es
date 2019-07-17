---
title: Clase nested_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: a568a8d9a3817883656406d63c3dd948539bb385
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268527"
---
# <a name="nestedexception-class"></a>Clase nested_exception

La clase describe una excepción para su uso con herencia múltiple. Captura la excepción controlada actualmente y lo almacena para su uso posterior.

## <a name="syntax"></a>Sintaxis

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>Funciones

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Se produce la excepción almacenada.|
|[nested_ptr](#nested_ptr)|Devuelve la excepción almacenada.|

### <a name="op_as"></a> operator=

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a> nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Valor devuelto

La excepción almacenada capturada por este `nested_exception` objeto.

### <a name="rethrow_nested"></a> rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Comentarios

Si `nested_ptr()` devuelve un puntero nulo, la función llama a `std::terminate()`. En caso contrario, inicia la excepción almacenada capturada por `*this`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exception>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[exception (Clase)](../standard-library/exception-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
