---
title: Error del compilador C2504 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fb11774f65454799761913babb428dc6a471743
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054134"
---
# <a name="compiler-error-c2504"></a>Error del compilador C2504

'class': clase base sin definir

La clase base se declara pero nunca se ha definido.  Causas posibles:

1. Falta el archivo de inclusión.

1. La clase base externa no se declara con [extern](../../cpp/using-extern-to-specify-linkage.md).

El ejemplo siguiente genera C2504:

```
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

DE ACUERDO

```
class C{};
class D : public C {};
```