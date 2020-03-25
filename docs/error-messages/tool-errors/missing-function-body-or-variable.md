---
title: Cuerpo de función o variable no encontrados
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6d2ef22b90009d320485fb6fe3f7e308ae05c442
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173626"
---
# <a name="missing-function-body-or-variable"></a>Cuerpo de función o variable no encontrados

Con solo un prototipo de función, el compilador puede continuar sin errores, pero el enlazador no puede resolver una llamada a una dirección porque no hay código de función o espacio de variables reservado. No verá este error hasta que cree una llamada a la función que el vinculador debe resolver.

## <a name="example"></a>Ejemplo

La llamada de función en Main producirá el error LNK2019 porque el prototipo permite que el compilador piense que la función existe.  El enlazador detecta que no es así.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Ejemplo

En C++, asegúrese de que incluye la implementación de una función específica para una clase y no solo un prototipo en la definición de clase. Si va a definir la clase fuera del archivo de encabezado, asegúrese de incluir el nombre de clase antes de la función (`Classname::memberfunction`).

```cpp
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>Consulte también

[Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
