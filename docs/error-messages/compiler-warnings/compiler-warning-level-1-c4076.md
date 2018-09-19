---
title: Del compilador (nivel 1) de la advertencia C4076 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f0a8066b8e79b75f3d5ede37f4e5ad6b61db168
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037884"
---
# <a name="compiler-warning-level-1-c4076"></a>Advertencia del compilador (nivel 1) C4076

> '*modificador de tipo*': no se puede usar con el tipo '*typename*'

## <a name="remarks"></a>Comentarios

Un modificador de tipo, ya sea **firmado** o **sin signo**, no se puede usar con un tipo no entero. *modificador de tipo* se omite.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4076; Para corregirlo, quite el **sin signo** modificador de tipo:

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```