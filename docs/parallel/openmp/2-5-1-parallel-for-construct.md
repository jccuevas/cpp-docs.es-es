---
title: 2.5.1 parallel for (construcción) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfff3b0c17dd098b5d802af61a7ca1f81cb02845
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373966"
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for (Construcción)

El **paralelas para** directiva es un acceso directo para un **paralelo** región que contiene una sola **para** directiva. La sintaxis de la **paralelas para** directiva es como sigue:

```
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Esta directiva permite que todas las cláusulas de la **paralelo** directiva y la **para** la directiva, excepto el `nowait` cláusula con significados idénticos y restricciones. La semántica es idéntica a la especificación explícita de un **paralelo** directiva seguido inmediatamente por un **para** directiva.

## <a name="cross-references"></a>Referencias cruzadas:

- **paralelo** la directiva, consulte [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.

- **para** la directiva, consulte [sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11.

- Cláusulas de atributos de datos, vea [2.7.2 cláusulas de atributos de uso compartido de datos](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.