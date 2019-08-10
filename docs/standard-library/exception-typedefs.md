---
title: '&lt;exception&gt; (Typedefs)'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: 58fc19b7cdf9656a4c2978a43a5c77092cc6716d
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916997"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt; (Typedefs)

## <a name="exception_ptr"></a>  exception_ptr

Tipo que describe un puntero a una excepción.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Comentarios

Clase interna sin especificar que se utiliza para implementar el tipo `exception_ptr`.

Utilice un objeto `exception_ptr` para hacer referencia a la excepción actual o a una instancia de una excepción especificada por el usuario. En la implementación de Microsoft, una excepción se representa mediante una estructura [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record). Cada objeto `exception_ptr` incluye un campo de referencia de excepción que apunta a una copia de la estructura `EXCEPTION_RECORD` que representa la excepción.

Cuando se declara una variable `exception_ptr`, la variable no está asociada a ninguna excepción. Es decir, su campo de referencia de excepción es NULL. Este tipo de objeto `exception_ptr` se denomina *exception_ptr null*.

Utilice la función `current_exception` o `make_exception_ptr` para asignar una excepción a un objeto `exception_ptr`. Cuando se asigna una excepción a una variable `exception_ptr`, el campo de referencia de excepción de la variable apunta a una copia de la excepción. Si no hay memoria suficiente para copiar la excepción, el campo de referencia de excepción apunta a una copia de una excepción [std::bad_alloc](../standard-library/bad-alloc-class.md). Si la `current_exception` función `make_exception_ptr` o no puede copiar la excepción por cualquier otro motivo, la función llama `terminate` a la función de CRT para salir del proceso actual.

A pesar de su nombre, un objeto `exception_ptr` no es en sí mismo un puntero. No obedece a la semántica de los punteros y no se puede usar con los operadores de acceso (`->`) o de direccionamiento indirecto (*) de miembro de puntero. El objeto `exception_ptr` no tiene ningún miembro de datos ni ninguna función miembro de tipo público.

**Comparaciones:**

Se pueden usar los operadores de igualdad (`==`) y desigualdad (`!=`) para comparar dos objetos `exception_ptr`. Los operadores no comparan el valor binario (patrón de bits) de las estructuras `EXCEPTION_RECORD` que representan las excepciones. En su lugar, los operadores comparan las indicaciones del campo de referencia de excepción de los objetos `exception_ptr`. Por tanto, un `exception_ptr` NULL y el valor NULL se consideran iguales.

## <a name="terminate_handler"></a>terminate_handler

El tipo describe un puntero a una función que se puede usar como `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Comentarios

El tipo describe un puntero a una función que se puede usar como controlador de finalización.

### <a name="example"></a>Ejemplo

Vea [set_terminate](../standard-library/exception-functions.md#set_terminate) para obtener un ejemplo de uso de `terminate_handler`.

## <a name="unexpected_handler"></a>unexpected_handler

El tipo describe un puntero a una función que se puede usar como un `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Ejemplo

Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de `unexpected_handler`.
