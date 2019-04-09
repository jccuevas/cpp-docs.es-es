---
title: Cuerpo de función o variable no encontrados
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: c287d804df3222475d7cf32c6eb025f642dfb913
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031866"
---
# <a name="missing-function-body-or-variable"></a>Cuerpo de función o variable no encontrados

Con un prototipo de función, el compilador puede continuar sin errores, pero el vinculador no puede resolver una llamada a una dirección porque no hay ningún código de función o variable espacio reservado. No verá este error hasta que cree una llamada a la función que el vinculador debe resolver.

## <a name="example"></a>Ejemplo

La llamada de función en main producirá el error LNK2019 porque el prototipo permite al compilador que cree que existe la función.  El vinculador busca que no es así.

```
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Ejemplo

En C++, asegúrese de que incluye la implementación de una función específica para una clase y no simplemente un prototipo en la definición de clase. Si va a definir la clase fuera del archivo de encabezado, no olvide incluir el nombre de clase antes de la función (`Classname::memberfunction`).

```
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

## <a name="see-also"></a>Vea también

[Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)