---
title: 4.4 OMP_NESTED | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1083269f31ebc710da24430635ff8381e3f2147a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419521"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

El `OMP_NESTED` variable de entorno habilita o deshabilita el paralelismo anidado a menos que el paralelismo anidado está habilitado o deshabilitado mediante una llamada a la `o` **mp_set_nested** rutina de biblioteca. Si establece en **TRUE**, paralelismo anidado está habilitado; si se establece en **FALSE**anidado paralelismo está deshabilitado. El valor predeterminado es **FALSE**.

Ejemplo:

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Referencia cruzada:

- `omp_set_nested` función, vea [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40.