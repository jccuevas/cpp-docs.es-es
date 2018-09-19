---
title: Error del compilador C2356 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2356
dev_langs:
- C++
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dfad1703b36e1cd995207d35b99b323c883f828
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065418"
---
# <a name="compiler-error-c2356"></a>Error del compilador C2356

el segmento de inicialización no debe cambiar durante la unidad de traducción

Causas posibles:

- `#pragma init_seg` precedido por el código de inicialización de segmento

- `#pragma init_seg` precedido por otro `#pragma init_seg`

Para resolver, mueva el código de inicialización del segmento al principio del módulo. Si se deben inicializar varias áreas, muévalos a módulos separados.

El ejemplo siguiente genera C2356:

```
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```