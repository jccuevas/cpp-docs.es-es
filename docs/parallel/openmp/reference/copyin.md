---
title: copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 424bb8eaa41e3bbb0cf697df108adcef116e1b04
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379586"
---
# <a name="copyin"></a>copyin

Permite que los subprocesos tener acceso a valor del subproceso principal, para un [threadprivate](../../../parallel/openmp/reference/threadprivate.md) variable.

## <a name="syntax"></a>Sintaxis

```
copyin(var)
```

## <a name="parameters"></a>Parámetros

*var*<br/>
El `threadprivate` variable que se inicializará con el valor de la variable en el subproceso principal, tal como existe antes de la construcción paralela.

## <a name="remarks"></a>Comentarios

`copyin` se aplica a las siguientes directivas:

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Secciones](../../../parallel/openmp/reference/sections-openmp.md)

Para obtener más información, consulte [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

## <a name="example"></a>Ejemplo

Consulte [threadprivate](../../../parallel/openmp/reference/threadprivate.md) para obtener un ejemplo del uso de `copyin`.

## <a name="see-also"></a>Vea también

[Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)