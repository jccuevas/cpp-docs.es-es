---
title: A.21 Variables de ámbito con la cláusula private | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7cdb4a7f-af24-44ac-9d33-e43840bc8f3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa68f0ebb5857e3f093e1985bd5f20105bb925c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392793"
---
# <a name="a21---scoping-variables-with-the-private-clause"></a>A.21 Variables de ámbito con la cláusula private

Los valores de `i` y `j` en el ejemplo siguiente no está definida en la salida de la región paralela:

```
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Para obtener más información sobre la `private` cláusula, vea [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25.