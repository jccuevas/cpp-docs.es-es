---
title: Error de las herramientas del vinculador LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ef9e3eae655a4fbee1c3da74f6036e5fb22434b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194621"
---
# <a name="linker-tools-error-lnk2028"></a>Error de las herramientas del vinculador LNK2028

"*exported_function*" (*decorated_name*) al que se hace referencia en la función "*function_containing_function_call*" (*decorated_name*)

## <a name="remarks"></a>Observaciones

Al intentar importar una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas difieren entre compilaciones nativas y puras.

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

## <a name="example"></a>Ejemplo

Este ejemplo de código genera un componente con una función exportada, nativa, cuya Convención de llamada se [__cdecl](../../cpp/cdecl.md)implícitamente.

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un cliente puro que utiliza la función nativa. Sin embargo, la Convención de llamada en **/clr: Pure** es [__clrcall](../../cpp/clrcall.md). En el ejemplo siguiente se genera LNK2028.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
