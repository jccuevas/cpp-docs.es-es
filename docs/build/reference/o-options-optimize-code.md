---
title: -O opciones) (optimizar código) | Documentos de Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
dev_langs:
- C++
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83ddebec9db7a02db40ef31c89c7ff48a66cf665
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376805"
---
# <a name="o-options-optimize-code"></a>/O (Opciones) (Optimizar código)

El **/O** opciones controlan diversas optimizaciones que le ayudarán a creación código para la velocidad máxima o el tamaño mínimo.

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) establece una combinación de las optimizaciones que generan código de tamaño mínimo.

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) establece una combinación de las optimizaciones que optimiza el código para la velocidad máxima.

- [/Ob](../../build/reference/ob-inline-function-expansion.md) controla la expansión de funciones inline.

- [/Od](../../build/reference/od-disable-debug.md) deshabilita la optimización, para acelerar la compilación y simplificar la depuración.

- [/ Og](../../build/reference/og-global-optimizations.md) habilita las optimizaciones globales.

- [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) genera funciones intrínsecas para las llamadas de función correspondiente.

- [/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) indica al compilador que dé prioridad a las optimizaciones de tamaño sobre las optimizaciones para acelerar el proceso.

- [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) (valor predeterminado) indica al compilador que dé prioridad a las optimizaciones de velocidad sobre las optimizaciones de tamaño.

- [/Ox](../../build/reference/ox-full-optimization.md) es una opción de combinación que selecciona varias de las optimizaciones con énfasis en la velocidad. Es un subconjunto estricto de la **/O2** optimizaciones.

- [/Oy](../../build/reference/oy-frame-pointer-omission.md) suprime la creación de punteros de marco en la pila de llamadas para acelerar las llamadas a función.

## <a name="remarks"></a>Comentarios

Puede combinar varios **/O** opciones en una instrucción única opción. Por ejemplo, **/Odi** es el mismo que **/Od /Oi**. Algunas opciones son mutuamente excluyentes y producen un error del compilador si se usan juntos. Vea el individuo **/O** opciones para obtener más información.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)   
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)