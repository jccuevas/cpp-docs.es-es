---
title: Error de las herramientas del vinculador LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 096ccb7ff443d24e0d53e73a5950faa1e85aeae6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194569"
---
# <a name="linker-tools-error-lnk2031"></a>Error de las herramientas del vinculador LNK2031

> no se puede generar p/Invoke para *decorated_name*'*function_declaration*'; falta la Convención de llamada en los metadatos

## <a name="remarks"></a>Observaciones

Al intentar importar una función nativa en una imagen pura, recuerde que las convenciones de llamada implícitas difieren entre compilaciones nativas y puras. Para obtener más información sobre las imágenes puras, consulte [código puro yC++comprobable (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

## <a name="example"></a>Ejemplo

Este ejemplo de código genera un componente con una función exportada, nativa, cuya Convención de llamada se [__cdecl](../../cpp/cdecl.md)implícitamente.

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un cliente puro que utiliza la función nativa. Sin embargo, la Convención de llamada en **/clr: Pure** es [__clrcall](../../cpp/clrcall.md). En el ejemplo siguiente se genera LNK2031.

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

En el ejemplo siguiente se muestra cómo utilizar la función nativa desde una imagen pura. Tenga en cuenta el especificador de Convención de llamada de **__cdecl** explícito.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
