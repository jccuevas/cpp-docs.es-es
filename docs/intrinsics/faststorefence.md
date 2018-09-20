---
title: __faststorefence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __faststorefence_cpp
- __faststorefence
dev_langs:
- C++
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5047dbb2023272ab03cc7d49f877f0fcc38a7b76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402192"
---
# <a name="faststorefence"></a>__faststorefence

**Específicos de Microsoft**

Garantiza que cada referencia de memoria anterior, incluidas las referencias de memoria de almacenamiento y de carga, sea visible globalmente antes que cualquier referencia de memoria posterior.

## <a name="syntax"></a>Sintaxis

```
void __faststorefence();
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__faststorefence`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Genera una secuencia de instrucciones de barrera de memoria completa que garantiza que las operaciones de almacenamiento y de carga emitidas antes que esta función intrínseca sean visibles globalmente antes de que continúe la ejecución. El efecto es comparable a la función intrínseca `_mm_mfence` en todas plataformas x64, pero más rápido.

En la plataforma AMD64, esta rutina genera una instrucción que actúa como una barrera de almacenamiento más rápida que la instrucción `sfence`. Para código crítico en el tiempo, use esta función intrínseca en lugar de `_mm_sfence` únicamente en plataformas AMD64. En plataformas Intel x64, la instrucción `_mm_sfence` es más rápida.

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)