---
title: Compilador advertencia (nivel 1) C4364 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e37c7f37e1b51296bd5c3ae2cbdb85a93326f027
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087258"
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