---
title: Enumeraciones (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: be11d8d8f38a92fbe4be00eed53dd5226bab0b59
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821758"
---
# <a name="enums-ccx"></a>Enumeraciones (C++/CX)

C++/CX admite la palabra clave `public enum class`, que es análoga a una C++ `scoped  enum`estándar. Cuando utilices un enumerador que se declara mediante la palabra clave `public enum class` , debes usar el identificador de enumeración para determinar el ámbito de cada valor de enumerador.

### <a name="remarks"></a>Notas

Una `public enum class` que no tiene un especificador de acceso, como `public`, se trata como una [enumeración con ámbito](../cpp/enumerations-cpp.md)de C++ estándar.

Una declaración `public enum class` o `public enum struct` puede tener un tipo subyacente de cualquier tipo entero, aunque el propio Windows Runtime requiere que el tipo sea Int32 o UInt32 para una enumeración Flags. La sintaxis siguiente describe las partes de un objeto `public enum class` o `public enum struct`.

En este ejemplo se muestra cómo definir una clase de enumeración pública:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

En este ejemplo siguiente se muestra cómo usarla:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Ejemplos

En los ejemplos siguientes se muestra cómo declarar una enumeración:

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

En el ejemplo siguiente se muestra cómo convertirla a equivalentes numéricos y realizar comparaciones. Observa que el ámbito del uso del enumerador `One` lo determina el identificador de la enumeración `Enum1` , y el ámbito del enumerador `First` lo determina `Enum2`.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Vea también

[Sistema de tipos](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
