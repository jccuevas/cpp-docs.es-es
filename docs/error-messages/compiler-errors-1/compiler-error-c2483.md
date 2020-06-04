---
title: Error del compilador C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205119"
---
# <a name="compiler-error-c2483"></a>Error del compilador C2483

>'*Identifier*': el objeto con el constructor o destructor no se puede declarar como ' Thread '

Este mensaje de error está obsoleto en Visual Studio 2015 y versiones posteriores. En versiones anteriores, las variables declaradas con el atributo `thread` no se pueden inicializar con un constructor u otra expresión que requiera la evaluación en tiempo de ejecución. Se requiere una expresión estática para inicializar los datos de `thread`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2483 en Visual Studio 2013 y versiones anteriores.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Consulte también

[thread](../../cpp/thread.md)
