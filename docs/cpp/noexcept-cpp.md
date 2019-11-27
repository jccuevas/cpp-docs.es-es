---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: 5e8d58ed246b0143dc3d3be545cd796a4c3d60ed
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245628"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++ 11:** Especifica si una función puede producir excepciones.

## <a name="syntax"></a>Sintaxis

> *noexception-Expression*: &nbsp;&nbsp;&nbsp;&nbsp;**noexception** &nbsp;&nbsp;&nbsp;&nbsp;**noexception (** *Constant-Expression* **)**

### <a name="parameters"></a>Parámetros

*expresión constante*<br/>
Expresión constante de tipo **bool** que representa si el conjunto de posibles tipos de excepción está vacío. La versión incondicional es equivalente a `noexcept(true)`.

## <a name="remarks"></a>Comentarios

Una *expresión noexception* es un tipo de *especificación de excepción*, un sufijo de una declaración de función que representa un conjunto de tipos que puede coincidir con un controlador de excepciones para cualquier excepción que sale de una función. Operador condicional unario `noexcept(`*constant_expression*`)` donde *constant_expression* produce **true**y su sinónimo incondicional **noexception**, especifica que el conjunto de posibles tipos de excepción que pueden salir de una función está vacío. Es decir, la función nunca produce una excepción y nunca permite que se propague una excepción fuera de su ámbito. El operador `noexcept(`*constant_expression*`)` donde *constant_expression* produce **false**o la ausencia de una especificación de excepción (distinta de para un destructor o una función de desasignación) indica que el conjunto de posibles excepciones que pueden salir de la función es el conjunto de todos los tipos.

Marque una función como **noexception** solo si todas las funciones a las que llama, ya sea directa o indirectamente, también son **noexception** o **const**. El compilador no comprueba necesariamente todas las rutas de acceso de código para las excepciones que podrían propagarse hasta una función **noexception** . Si una excepción sale del ámbito externo de una función marcada `noexcept`, se invoca a [STD:: Terminate](../standard-library/exception-functions.md#terminate) inmediatamente y no hay ninguna garantía de que se invoquen los destructores de los objetos en el ámbito. Utilice **noexception** en lugar del especificador de excepción dinámica `throw()`, que ahora está en desuso en el estándar. Se recomienda aplicar `noexcept` a cualquier función que nunca permita que una excepción se propague hacia arriba en la pila de llamadas. Cuando una función se declara **noexception**, permite que el compilador genere código más eficaz en varios contextos diferentes. Para obtener más información, vea [Especificaciones de excepciones](exception-specifications-throw-cpp.md).

## <a name="example"></a>Ejemplo

Una función de plantilla que copia su argumento se podría declarar **noexception, excepto** en la condición de que el objeto que se va a copiar sea un tipo de datos anterior (POD) sin formato. Este tipo de función podría declararse de este modo:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Vea también

[Prácticas C++ recomendadas modernas para excepciones y control de errores](errors-and-exception-handling-modern-cpp.md)<br/>
[Especificaciones de excepciones (Throw, noexception)](exception-specifications-throw-cpp.md)