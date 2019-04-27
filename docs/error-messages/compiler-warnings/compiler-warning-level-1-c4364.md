---
title: Advertencia del compilador (nivel 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: db2774b6a73a989b4e9250719f99122826b486fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207113"
---
# <a name="compiler-warning-level-1-c4364"></a>Advertencia del compilador (nivel 1) C4364

\#para el ensamblado 'archivo' ya aparecía previamente en la ubicación (número_de_línea) sin el atributo as_friend; as_friend que no se aplica

Un `#using` directiva se repitió en un archivo de metadatos determinado, pero la `as_friend` calificador no se usó en la primera aparición; el compilador omitirá el segundo `as_friend`.

Para obtener más información, consulte [ensamblados Friend (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un componente.

```
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4364.

```
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```