---
title: Las herramientas del vinculador LNK2028 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2028
dev_langs:
- C++
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9c8eaa03927f51acd3c3d84731e9ef2b282b7c6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704159"
---
# <a name="linker-tools-error-lnk2028"></a>Error de las herramientas del vinculador LNK2028

"*exported_function*" (*decorated_name*) al que hace referencia en la función "*function_containing_function_call*" (*decorated_name*)

## <a name="remarks"></a>Comentarios

Al intentar importar una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas son diferentes entre compilaciones nativas y puras.

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

## <a name="example"></a>Ejemplo

Este ejemplo de código genera un componente con una función exportada y nativa, cuya convención de llamada es implícitamente [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente crea a un cliente puro que usa la función nativa. Sin embargo, la convención de llamada en **/CLR: pure** es [__clrcall](../../cpp/clrcall.md). El ejemplo siguiente genera el error LNK2028.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```