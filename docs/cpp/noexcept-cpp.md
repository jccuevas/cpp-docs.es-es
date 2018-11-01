---
title: noexcept (C++)
ms.date: 01/12/2018
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: c314b554abb6c10e62b143f554777af50267e4e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620537"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C ++ 11:** especifica si una función podría generar excepciones.

## <a name="syntax"></a>Sintaxis

> *expresión de noexcept*: &nbsp; &nbsp; &nbsp; &nbsp; **noexcept** &nbsp; &nbsp; &nbsp; &nbsp; **noexcept (** *expresión-constante* **)**

### <a name="parameters"></a>Parámetros

*expresión constante*<br/>
Una expresión constante de tipo **bool** que indica si el conjunto de posibles tipos de excepción está vacío. La versión incondicional es equivalente a `noexcept(true)`.

## <a name="remarks"></a>Comentarios

Un *noexcept expresión* es una especie de *especificación de excepción*, un sufijo a una declaración de función que representa un conjunto de tipos que puede hacerse coincidir con un controlador de excepciones para cualquier excepción que se cierra un función. Operador condicional unario `noexcept(` *constant_expression* `)` donde *constant_expression* yeilds **true**y su sinónimo incondicional **noexcept**, especificar que el conjunto de posibles tipos de excepción que se puede salir de una función está vacío. Es decir, la función nunca produce una excepción y no permite nunca una excepción que se propaguen fuera de su ámbito. El operador `noexcept(` *constant_expression* `)` donde *constant_expression* yeilds **false**, o la ausencia de una especificación de excepción (más allá de una función de destructor o desasignación), indica que el conjunto de posibles excepciones que pueden salir de la función es el conjunto de todos los tipos.

Marque una función como **noexcept** sólo si todas las funciones que llama, directa o indirectamente, también son **noexcept** o **const**. El compilador no comprueba necesariamente cada ruta de acceso del código para las excepciones que podrían ascender hasta una **noexcept** función. Si una excepción salir del ámbito exterior de una función marcada `noexcept`, [std:: Terminate](../standard-library/exception-functions.md#terminate) se invoca inmediatamente, y no hay ninguna garantía de que se invocará los destructores de todos los objetos dentro del ámbito. Use **noexcept** en lugar del especificador de excepción dinámicas `throw()`, que ahora está en desuso en el estándar. Le recomendamos que aplique `noexcept` a cualquier función que no se permite nunca una excepción se propague hacia arriba de la pila de llamadas. Cuando se declara una función **noexcept**, permite al compilador que genere código más eficaz en varios contextos distintos. Para obtener más información, consulte [las especificaciones de excepción](exception-specifications-throw-cpp.md).

## <a name="example"></a>Ejemplo

Una función de plantilla que copia su argumento podría declararse **noexcept** la condición de que el objeto que se va a copiar es un tipo de datos antiguos sin formato (POD). Este tipo de función podría declararse de este modo:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Vea también

[Control de excepciones de C++](cpp-exception-handling.md)<br/>
[Especificaciones de excepciones (throw, noexcept)](exception-specifications-throw-cpp.md)