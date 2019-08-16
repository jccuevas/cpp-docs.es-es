---
title: Compilador advertencia (nivel 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 09ea9e2963735c1e011e25b42b04ad6d67d084a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349820"
---
# <a name="compiler-warning-level-2-c4099"></a>Compilador advertencia (nivel 2) C4099

'identifier': nombre de tipo visto anteriormente usando 'tipodeobjeto1' ahora se ve usando 'objecttype2'

Un objeto declarado como una estructura se define como una clase o un objeto declarado como una clase se define como una estructura. El compilador usa el tipo especificado en la definición.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4099.

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```