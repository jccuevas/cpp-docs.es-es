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
ms.openlocfilehash: 09348d061fde4cb09eb6eb351f146404f355e184
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187796"
---
# <a name="__uuidof-operator"></a>__uuidof (Operador)

**Específicos de Microsoft**

Recupera el GUID asociado a la expresión.

## <a name="syntax"></a>Sintaxis

```
__uuidof (expression)
```

## <a name="remarks"></a>Observaciones

La *expresión* puede ser un nombre de tipo, un puntero, una referencia o una matriz de ese tipo, una plantilla especializada en estos tipos o una variable de estos tipos. El argumento es válido siempre y cuando el compilador pueda utilizarlo para encontrar el GUID asociado.

Un caso especial de este intrínseco es cuando se proporciona **0** o NULL como argumento. En este caso, **__uuidof** devolverá un GUID formado por ceros.

Utilice esta palabra clave para extraer el GUID asociado a lo siguiente:

- Objeto por el atributo extendido [UUID](../cpp/uuid-cpp.md) .

- Bloque de biblioteca creado con el atributo [Module](../windows/attributes/module-cpp.md) .

> [!NOTE]
> En una compilación de depuración, **__uuidof** siempre Inicializa un objeto dinámicamente (en tiempo de ejecución). En una compilación de versión, **__uuidof** puede estáticamente (en tiempo de compilación) inicializar un objeto.

Por compatibilidad con versiones anteriores, **_uuidof** es un sinónimo de **__uuidof** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

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

En los casos en los que el nombre de la biblioteca ya no está en el ámbito, puede usar `__LIBID_` en lugar de **__uuidof**. Por ejemplo:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
