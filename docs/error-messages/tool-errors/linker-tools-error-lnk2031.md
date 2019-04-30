---
title: Error de las herramientas del vinculador LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 003b9a58bfb08130f034530f59e2de27efa2ae8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298924"
---
# <a name="linker-tools-error-lnk2031"></a>Error de las herramientas del vinculador LNK2031

> no se puede generar p/invoke para "*function_declaration*" *decorated_name*; no se encuentra en los metadatos de convención de llamada

## <a name="remarks"></a>Comentarios

Cuando se intenta importar una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas difieren entre compilaciones nativas y puras. Para obtener más información acerca de las imágenes puras, vea [código puro y comprobable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

## <a name="example"></a>Ejemplo

Este ejemplo de código genera un componente con una función exportada, native, cuya convención de llamada es implícitamente [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente crea a un cliente puro que utiliza la función nativa. Sin embargo, la convención de llamada en **/CLR: pure** es [__clrcall](../../cpp/clrcall.md). El ejemplo siguiente genera el error LNK2031.

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

El ejemplo siguiente muestra cómo utilizar la función nativa de una imagen pura. Tenga en cuenta la configuración explícita **__cdecl** especificador de convención de llamada.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```