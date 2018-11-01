---
title: Error del compilador C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 04d41a50bc0d5e811e47e5f9d146362a543f26f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445700"
---
# <a name="compiler-error-c2170"></a>Error del compilador C2170

'identifier': no se declara como una función, no puede ser intrínseco

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Pragma `intrinsic` se utiliza para un elemento que no sea una función.

1. Pragma `intrinsic` se usa para una función sin forma intrínseca.