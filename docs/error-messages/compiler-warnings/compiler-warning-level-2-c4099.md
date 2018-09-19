---
title: Compilador advertencia (nivel 2) C4099 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d7ffee02e8e5414a0e06cc4ba0da77a50c75f53
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110177"
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