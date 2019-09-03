---
title: loop (Pragma)
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: 013540ffe120f42c15538ce86661753b9cf9416f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220849"
---
# <a name="loop-pragma"></a>loop (Pragma)

Controla cómo se debe tener en cuenta el código de bucle por la paralelizador automático automática o excluye un bucle de la consideración del vectorizador automático automático.

## <a name="syntax"></a>Sintaxis

> **bucle #pragma (hint_parallel (** *n* **))** \
> **bucle #pragma (no_vector)** \
> **bucle #pragma (ivdep)**

### <a name="parameters"></a>Parámetros

**hint_parallel (** *n* **)** \
Sugerencia al compilador de que este bucle se debe paralelizar en *n* subprocesos, donde *n* es un literal entero positivo o cero. Si *n* es cero, se utiliza el número máximo de subprocesos en tiempo de ejecución. Es una sugerencia para el compilador, no un comando. No hay ninguna garantía de que el bucle se vaya a ejecutar en paralelo. Si el bucle tiene dependencias de datos, o problemas estructurales, no se ejecutará en paralelo. Por ejemplo, no está en paralelo Si almacena en un valor escalar que se usa más allá del cuerpo del bucle.

El compilador omite esta opción a menos que se especifique el modificador del compilador [/QPAR](../build/reference/qpar-auto-parallelizer.md)

**no_vector**\
De forma predeterminada, los intentos de vectorizador automático automáticos intentan vectorizar todos los bucles que evalúa pueden beneficiarse de él. Especifique esta pragma para deshabilitar la vectorizador automático automática del bucle siguiente.

**ivdep**\
Sugerencia para que el compilador omita las dependencias vectoriales para este bucle. Use esta opción junto con **hint_parallel**.

## <a name="remarks"></a>Comentarios

Para usar la Directiva pragma **Loop** , colóquela inmediatamente antes de, no en, una definición de bucle. La directiva pragma surte efecto para el ámbito del bucle que aparece detrás. Puede aplicar varias directivas pragma a un bucle, en cualquier orden, pero debe establecer cada una de ellas en una instrucción pragma diferente.

## <a name="see-also"></a>Vea también

[Paralelización automática y vectorización automática](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
