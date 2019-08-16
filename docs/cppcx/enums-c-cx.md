---
title: Enumeraciones (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: f16a288a0b928b74ef42de5781fd1b54930927d6
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345816"
---
# <a name="enums-ccx"></a>Enumeraciones (C++/CX)

C++ / c++ / CX admite el `public enum class` palabra clave, que es análogo a un estándar de C++ `scoped  enum`. Cuando utilices un enumerador que se declara mediante la palabra clave `public enum class` , debes usar el identificador de enumeración para determinar el ámbito de cada valor de enumerador.

### <a name="remarks"></a>Comentarios

Una `public enum class` que no tiene un especificador de acceso, como `public`, se trata como una [enumeración con ámbito](../cpp/enumerations-cpp.md)de C++ estándar.

Un `public enum class` o `public enum struct` declaración puede tener un tipo subyacente de cualquier tipo entero aunque el propio tiempo de ejecución de Windows requiere que el tipo sea int32, o uint32 para una enumeración de marcas. La sintaxis siguiente describe las partes de un objeto `public enum class` o `public enum struct`.

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
[Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
