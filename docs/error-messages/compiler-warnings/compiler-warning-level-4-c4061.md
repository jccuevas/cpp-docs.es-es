---
title: Del compilador (nivel 4) de la advertencia C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 073e3e9cb1cb5bb6b0f66157c986072227960212
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401428"
---
# <a name="compiler-warning-level-4-c4061"></a>Del compilador (nivel 4) de la advertencia C4061

> enumerador '*identificador*'en el conmutador de la enumeración'*enumeración*' no está controlado de forma explícita por una etiqueta de caso

El enumerador especificado *identificador* tiene asociado ningún controlador un `switch` instrucción que tenga un `default` caso. El caso de que falta puede ser un descuido, o puede que no sea un problema. Puede depender de si el enumerador está controlado por el caso predeterminado o no. Para una advertencia relacionada con los enumeradores no utilizadas en `switch` las instrucciones que no tienen ningún `default` case, consulte [C4062](compiler-warning-level-4-c4062.md).

De forma predeterminada, esta advertencia está desactivada. Para obtener más información acerca de cómo habilitar las advertencias que están desactivadas de forma predeterminada, consulte [compilador advertencias que están desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4061; Agregar un caso del enumerador que faltan corregir:

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>Vea también

[Advertencia del compilador (nivel 4) C4062](compiler-warning-level-4-c4062.md)
