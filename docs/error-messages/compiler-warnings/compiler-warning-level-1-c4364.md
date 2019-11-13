---
title: ADVERTENCIA del compilador (nivel 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 716f440cddc3889ec719ef3b295a0d076175be93
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966518"
---
# <a name="compiler-warning-level-1-c4364"></a>ADVERTENCIA del compilador (nivel 1) C4364

\#usar para el ensamblado ' archivo ' anteriormente visible en la ubicación (line_number) sin as_friend atributo; as_friend no aplicado

Se repitió una directiva de `#using` para un archivo de metadatos determinado, pero el calificador de `as_friend` no se usó en la primera aparición; el compilador omitirá el segundo `as_friend`.

Para obtener más información, vea [ensambladosC++de confianza ()](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un componente.

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4364.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```