---
title: Compilador advertencia (nivel 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 09ea9e2963735c1e011e25b42b04ad6d67d084a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471726"
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