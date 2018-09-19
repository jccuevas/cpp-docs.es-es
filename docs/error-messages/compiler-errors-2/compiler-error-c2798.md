---
title: Error del compilador C2798 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2798
dev_langs:
- C++
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88241989d54e1a068b226b59091a381f531dee9e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028862"
---
# <a name="compiler-error-c2798"></a>Error del compilador C2798

'super:: miembro' es ambiguo

Varias estructuras heredadas que contienen el miembro al que hace referencia con [super](../../cpp/super.md). Puede resolver el error, ya sea por:

- Quitar de la lista de herencia de D. B1 o B2

- Cambiar el nombre del miembro de datos en la vitamina B1 o B2.

El ejemplo siguiente genera C2798:

```
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```