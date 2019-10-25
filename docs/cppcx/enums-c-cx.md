---
title: Enumeraciones (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 3bdcff03872dcfe83f0be5752cec4f567fbc6b72
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740214"
---
# <a name="enums-ccx"></a>Enumeraciones (C++/CX)

C++/CX admite la `public enum class` palabra clave, que se análogo a un C++ `scoped  enum`estándar. Cuando utilices un enumerador que se declara mediante la palabra clave `public enum class` , debes usar el identificador de enumeración para determinar el ámbito de cada valor de enumerador.

### <a name="remarks"></a>Comentarios

Una `public enum class` que no tiene un especificador de acceso, como `public`, se trata como una [enumeración con ámbito](../cpp/enumerations-cpp.md)de C++ estándar.

Una `public enum class` declaración `public enum struct` o puede tener un tipo subyacente de cualquier tipo entero, aunque el propio Windows Runtime requiere que el tipo sea Int32 o UInt32 para una enumeración de marcas. La sintaxis siguiente describe las partes de un objeto `public enum class` o `public enum struct`.

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
