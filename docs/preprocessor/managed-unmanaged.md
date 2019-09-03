---
title: managed, unmanaged (Pragmas)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 4c13155d1c84966a593df11baf525a0c3539f02c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218814"
---
# <a name="managed-unmanaged-pragmas"></a>managed, unmanaged (Pragmas)

Habilite el control de nivel de función para compilar funciones como administradas o no administradas.

## <a name="syntax"></a>Sintaxis

> **#pragma administrado**\
> **#pragma no administrado**\
> **#pragma administrado (** [ **inserciones,** ] { **on** | **OFF** } **)** \
> **#pragma administrado (pop)**

## <a name="remarks"></a>Comentarios

La opción del compilador [/CLR](../build/reference/clr-common-language-runtime-compilation.md) proporciona un control de nivel de módulo para compilar funciones como administradas o no administradas.

Una función no administrada se compilará para la plataforma nativa. La ejecución de esa parte del programa se pasará a la plataforma nativa mediante el Common Language Runtime.

Las funciones se compilan como administradas de forma predeterminada cuando se utiliza `/clr`.

Al aplicar estas pragmas:

- Agregue la pragma que precede a una función, pero no dentro de un cuerpo de función.

- Agregue la pragma después de las instrucciones `#include`. No utilice estas pragmas antes `#include` de las instrucciones.

El compilador omite las pragmas administradas y **no** administradas `/clr` si no se utiliza en la compilación.

Cuando se crea una instancia de una función de plantilla, el estado de pragma cuando se define la plantilla determina si está administrada o no administrada.

Para obtener más información, vea [inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md).

## <a name="example"></a>Ejemplo

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
