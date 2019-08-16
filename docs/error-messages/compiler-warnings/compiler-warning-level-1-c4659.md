---
title: Advertencia del compilador (nivel 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 2aef25e922d8f38ac7103b1b12ccb31c282f0403
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374656"
---
# <a name="compiler-warning-level-1-c4659"></a>Advertencia del compilador (nivel 1) C4659

\#pragma 'pragma': uso del segmento reservado 'segmento' tiene un comportamiento indefinido, utilice #pragma comment (linker,...)

La opción .drectve se usó para pasar una opción al vinculador. En su lugar, utilice la directiva pragma [comentario](../../preprocessor/comment-c-cpp.md) para pasar una opción del vinculador.

```
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```