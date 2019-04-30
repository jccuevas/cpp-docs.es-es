---
title: bucle
ms.date: 10/18/2018
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: a1640881d98073381a941478f4b78177a95698d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411336"
---
# <a name="loop"></a>bucle

Controla cómo el paralelizador automático debe considerar el código del bucle y/o excluye un bucle de la consideración del vectorizador automático.

## <a name="syntax"></a>Sintaxis

```
#pragma loop( hint_parallel(n) )
#pragma loop( no_vector )
#pragma loop( ivdep )
```

### <a name="parameters"></a>Parámetros

*hint_parallel(n)*<br/>
Sugiere al compilador que este bucle se ejecute en paralelo a través de *n* subprocesos, donde *n* es un literal entero positivo o cero. Si *n* es cero, se usa el número máximo de subprocesos en tiempo de ejecución. Esta es una sugerencia que se hace al compilador, no una orden y, por tanto, no existen garantías de que el bucle se ejecute en paralelo. Si el bucle tiene dependencias de datos o problemas estructurales (por ejemplo, el bucle se almacena en un valor escalar que se usa más allá del cuerpo del bucle), el bucle no se ejecuta en paralelo.

El compilador omite esta opción a menos que el [/Qpar](../build/reference/qpar-auto-parallelizer.md) ha especificado el modificador del compilador.

*no_vector*<br/>
De forma predeterminada, el vectorizador automático está activado e intentará vectorizar todos los bucles que evalúe de modo que se beneficien de él. Especifique esta directiva pragma para deshabilitar el vectorizador automático para el bucle que aparece detrás.

*ivdep*<br/>
Sugiere al compilador que omita las dependencias de vector de este bucle. Utilícelo en conjunción con *hint_parallel*.

## <a name="remarks"></a>Comentarios

Para usar el **bucle** pragma, lo coloca inmediatamente antes, no en: una definición de bucle. La directiva pragma surte efecto para el ámbito del bucle que aparece detrás. Puede aplicar varias directivas pragma a un bucle, en cualquier orden, pero debe establecer cada una de ellas en una instrucción pragma diferente.

## <a name="see-also"></a>Vea también

[Paralelización y vectorización automáticas](../parallel/auto-parallelization-and-auto-vectorization.md)<br/>
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)