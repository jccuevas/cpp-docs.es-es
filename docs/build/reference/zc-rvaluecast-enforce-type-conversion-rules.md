---
title: /Zc:rvalueCast (Exigir reglas de conversión de tipos)
ms.date: 02/18/2020
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: ac74192cad8a62e4c82b480038e727b114362cdd
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504572"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Exigir reglas de conversión de tipos)

Cuando se especifica la opción **`/Zc:rvalueCast`** , el compilador identifica correctamente un tipo de referencia rvalue como el resultado de una operación de conversión. Su comportamiento se ajusta al estándar de C++ 11. Cuando no se especifica la opción, el comportamiento del compilador es el mismo que en Visual Studio 2012.

## <a name="syntax"></a>Sintaxis

> **`/Zc:rvalueCast`**\
> **`/Zc:rvalueCast-`**

## <a name="remarks"></a>Observaciones

Si se especifica **`/Zc:rvalueCast`** , el compilador sigue la sección 5,4 del estándar c++ 11 y trata únicamente las expresiones de conversión que dan lugar a tipos que no son de referencia y expresiones de conversión que dan lugar a referencias rvalue a tipos que no son de función como tipos rvalue. De forma predeterminada, o si se especifica **`/Zc:rvalueCast-`** , el compilador no se ajusta y trata todas las expresiones de conversión que dan lugar a referencias rvalue como rvalues. En cuanto al cumplimiento y para eliminar los errores en el uso de conversiones, se recomienda utilizar **`/Zc:rvalueCast`** .

De forma predeterminada, **`/Zc:rvalueCast`** está desactivado ( **`/Zc:rvalueCast-`** ). La opción del compilador [/permissive-](permissive-standards-conformance.md) establece implícitamente esta opción, pero se puede invalidar mediante el uso de **`/Zc:rvalueCast-`** .

Use **`/Zc:rvalueCast`** si pasa una expresión de conversión como argumento a una función que toma un tipo de referencia rvalue. El comportamiento predeterminado produce el error del compilador [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) cuando el compilador determina incorrectamente el tipo de la expresión de conversión. En este ejemplo se muestra un error del compilador en el código correcto cuando no se especifica **`/Zc:rvalueCast`** :

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

Puede que el comportamiento predeterminado del compilador no notifique el error C2102 cuando proceda. En este ejemplo, el compilador no notifica un error si se toma la dirección de un valor r creado por una conversión de identidad cuando no se especifica **`/Zc:rvalueCast`** :

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione las **propiedades de configuración** > página de propiedades del **lenguaje** **CC++ /**  > .

1. Establezca la propiedad **exigir reglas de conversión de tipos** en **`/Zc:rvalueCast`** o **`/Zc:rvalueCast-`** . Elija **Aceptar** o **aplicar** para guardar los cambios.

## <a name="see-also"></a>Consulte también

[/Zc (Ajuste)](zc-conformance.md)
