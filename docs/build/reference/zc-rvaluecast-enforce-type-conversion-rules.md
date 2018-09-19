---
title: '/ Zc: rvaluecast (exigir reglas de conversión de tipos) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 626cabbec169d541a63dd65c22a7380718613b79
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706594"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Exigir reglas de conversión de tipos)

Cuando el **/Zc: rvaluecast** se especifica la opción, el compilador identifica correctamente un tipo de referencia rvalue como resultado de una operación de conversión según el estándar C ++ 11. Cuando no se especifica la opción, el comportamiento del compilador es el mismo que en Visual Studio 2012.

## <a name="syntax"></a>Sintaxis

> **/Zc:rvalueCast**[**-**]

## <a name="remarks"></a>Comentarios

Si **/Zc: rvaluecast** se especifica, el compilador sigue la sección 5.4 del estándar C ++ 11 y trata sólo de expresiones que producen tipos sin referencia y las expresiones que producen las referencias rvalue para tipos de función no puede convertir de conversión como tipos de valor r. De forma predeterminada, o si **/Zc:rvalueCast-** se especifica, el compilador no es conforme y trata todas las expresiones de conversión que resultan en referencias a valor r como valores r. Para conformidad y eliminar los errores en el uso de conversiones, recomendamos que use **/Zc: rvaluecast**.

De forma predeterminada, **/Zc: rvaluecast** está desactivado (**/Zc:rvalueCast-**). El [/ permissive-](permissive-standards-conformance.md) opción del compilador implícitamente establece esta opción, pero se pueden invalidar utilizando **/Zc:rvalueCast-**.

Use **/Zc: rvaluecast** si pasa una expresión de conversión como argumento a una función que toma un tipo de referencia rvalue. El comportamiento predeterminado genera el error del compilador [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) cuando el compilador determina incorrectamente el tipo de la expresión de conversión. Este ejemplo muestra un error del compilador correcto en el código cuando **/Zc: rvaluecast** no se especifica:

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

Puede que el comportamiento predeterminado del compilador no notifique el error C2102 cuando proceda. En este ejemplo, el compilador no notifica un error si se toma la dirección de un valor r creado por una conversión de identidad cuando **/Zc: rvaluecast** no se especifica:

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: rvaluecast** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
