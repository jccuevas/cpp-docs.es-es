---
title: OMP_NESTED | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c90878ce96cf1639c983be899ba13eccf1f040e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376552"
---
# <a name="ompnested"></a>OMP_NESTED

Especifica si está habilitado paralelismo anidado, a menos que está habilitado o deshabilitado con paralelismo anidado `omp_set_nested`.

## <a name="syntax"></a>Sintaxis

```
set OMP_NESTED[=TRUE | =FALSE]
```

## <a name="remarks"></a>Comentarios

El `OMP_NESTED` variable de entorno puede reemplazarse por la [omp_set_nested ()](../../../parallel/openmp/reference/omp-set-nested.md) función.

El valor predeterminado de la implementación de Visual C++ del estándar OpenMP es `OMP_DYNAMIC=FALSE`.

Para obtener más información, consulte [OMP_NESTED 4.4](../../../parallel/openmp/4-4-omp-nested.md).

## <a name="example"></a>Ejemplo

El comando siguiente establece la `OMP_NESTED` variable de entorno en TRUE:

```
set OMP_NESTED=TRUE
```

El comando siguiente muestra la configuración actual de la `OMP_NESTED` variable de entorno:

```
set OMP_NESTED
```

## <a name="see-also"></a>Vea también

[Variables de entorno](../../../parallel/openmp/reference/openmp-environment-variables.md)