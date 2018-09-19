---
title: Error del compilador C2500 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b7e24ca520796b63171fe63c2bf841fe8776845
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026678"
---
# <a name="compiler-error-c2500"></a>Error del compilador C2500

'identificador1': 'identificador2' ya es una clase base directa

Una clase o estructura aparece más de una vez en una lista de clases bases.

Una base directa es una mencionadas en la lista base. Una base indirecta es una clase base de una de las clases en la lista base.

Una clase no puede especificarse más de una vez como una clase base directa. Una clase puede utilizarse como una clase base indirecta más de una vez.

El ejemplo siguiente genera C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```