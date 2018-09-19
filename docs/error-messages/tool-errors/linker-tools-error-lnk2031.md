---
title: Las herramientas del vinculador LNK2031 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86ea6da8a73d9ba2427e9455c4fca87cd32dd2b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703670"
---
# <a name="linker-tools-error-lnk2031"></a>Error de las herramientas del vinculador LNK2031

> no se puede generar p/invoke para "*function_declaration*" *decorated_name*; falta en los metadatos de convención de llamada

## <a name="remarks"></a>Comentarios

Al intentar importar una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas son diferentes entre compilaciones nativas y puras. Para obtener más información acerca de las imágenes puras, vea [código puro y comprobable (C++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

## <a name="example"></a>Ejemplo

Este ejemplo de código genera un componente con una función exportada y nativa, cuya convención de llamada es implícitamente [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente crea a un cliente puro que usa la función nativa. Sin embargo, la convención de llamada en **/CLR: pure** es [__clrcall](../../cpp/clrcall.md). El ejemplo siguiente genera el error LNK2031.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo utilizar la función nativa de una imagen pura. Tenga en cuenta la explícita **__cdecl** especificador de convención de llamada.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```