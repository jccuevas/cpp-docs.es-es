---
title: Error de las herramientas del vinculador LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ed2dc1a95d4dd7c447b360da21b5046e20f79083
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298989"
---
# <a name="linker-tools-error-lnk2028"></a>Error de las herramientas del vinculador LNK2028

"*exported_function*" (*decorated_name*) al que hace referencia en la función "*function_containing_function_call*" (*decorated_name*)

## <a name="remarks"></a>Comentarios

Cuando se intenta importar una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas difieren entre compilaciones nativas y puras.

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

## <a name="example"></a>Ejemplo

Este ejemplo de código genera un componente con una función exportada, native, cuya convención de llamada es implícitamente [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente crea a un cliente puro que utiliza la función nativa. Sin embargo, la convención de llamada en **/CLR: pure** es [__clrcall](../../cpp/clrcall.md). El ejemplo siguiente genera el error LNK2028.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```