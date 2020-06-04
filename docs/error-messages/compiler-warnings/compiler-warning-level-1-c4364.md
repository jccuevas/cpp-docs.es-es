---
title: Advertencia del compilador (nivel 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 79c8809b4de9d6853aaacec4283bf01d0e89305e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187107"
---
# <a name="compiler-warning-level-1-c4364"></a>Advertencia del compilador (nivel 1) C4364

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
