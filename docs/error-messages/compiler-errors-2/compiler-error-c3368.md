---
title: Error del compilador C3368 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3368
dev_langs:
- C++
helpviewer_keywords:
- C3368
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 236bfdfc031544e05d4aa95d9c36720ddb0ebdf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051303"
---
# <a name="compiler-error-c3368"></a>Error del compilador C3368

'declaración de función': convención de llamada no válida para IDL

Solo se pueden usar las convenciones de llamada [__stdcall](../../cpp/stdcall.md) o [__cdecl](../../cpp/cdecl.md) en un archivo .idl.

El ejemplo siguiente genera la advertencia C3368:

```
// C3368.cpp
// processor: x86
[idl_module(name="Name", dllname="Some.dll")];

[idl_module(name="Name")]
int __fastcall f1();   // C3368
```