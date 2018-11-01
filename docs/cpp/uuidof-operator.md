---
title: __uuidof (Operador)
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: 6e593d023c486aa504f0b5eee8578fa8c307bcc8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432713"
---
# <a name="uuidof-operator"></a>__uuidof (Operador)

**Específicos de Microsoft**

Recupera el GUID asociado a la expresión.

## <a name="syntax"></a>Sintaxis

```
__uuidof (expression)
```

## <a name="remarks"></a>Comentarios

El *expresión* puede ser un nombre de tipo, puntero, referencia o matriz de ese tipo, una plantilla especializada en estos tipos, o una variable de estos tipos. El argumento es válido siempre y cuando el compilador pueda utilizarlo para encontrar el GUID asociado.

Un caso especial de este intrínseco es cuando cualquier **0** o NULL se proporciona como argumento. En este caso, **__uuidof** devolverá un GUID compuesto de ceros.

Utilice esta palabra clave para extraer el GUID asociado a lo siguiente:

- Un objeto por el [uuid](../cpp/uuid-cpp.md) atributo extendido.

- Un bloque de biblioteca creado con el [módulo](../windows/module-cpp.md) atributo.

> [!NOTE]
> En una compilación de depuración, **__uuidof** siempre Inicializa un objeto dinámicamente (en tiempo de ejecución). En una versión de lanzamiento, **__uuidof** puede inicializar estáticamente (en tiempo de compilación) un objeto.

Para ofrecer compatibilidad con versiones anteriores, **_uuidof** es un sinónimo de **__uuidof** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) es especificado.

## <a name="example"></a>Ejemplo

El código siguiente (compilado con ole32.lib) mostrará el uuid de un bloque de biblioteca creado con el atributo module:

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>Comentarios

En casos donde el nombre de biblioteca ya no está en el ámbito, puede usar `__LIBID_` en lugar de **__uuidof**. Por ejemplo:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)