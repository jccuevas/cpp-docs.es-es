---
title: Opciones -Q (operaciones de bajo nivel) | Documentos de Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /q
dev_langs:
- C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a18c5d790cf21e8eb130a2b2baa152e20d79a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375040"
---
# <a name="q-options-low-level-operations"></a>/Q (Opciones) (Operaciones de bajo nivel)

Puede usar el **/q** opciones del compilador para realizar las siguientes operaciones de compilador de bajo nivel:

- [/ Qfast_transcendentals (Force funciones transcendentales rápidas)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): genera funciones transcendentales rápidas.

- [/QIfist (suprimir _ftol)](../../build/reference/qifist-suppress-ftol.md): suprime `_ftol` cuando una conversión de un tipo de punto flotante a un tipo entero es necesaria (sólo x86).

- [/ Qimprecise_fwaits (quitar comandos fwait en los bloques Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): quita `fwait` comandos dentro de `try` bloques.

- [/Qpar (Paralelizador automático)](../../build/reference/qpar-auto-parallelizer.md): habilita la paralelización automática de bucles marcados con el [#pragma loop()](../../preprocessor/loop.md) directiva.

- [/ Qpar-report (nivel de información de Paralelizador automático)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): habilita los niveles de ejecución en paralelo automática de informe.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): suprime las optimizaciones de registro de punto flotante carga y para mover entre la memoria y MMX registra.

- [/ Qspectre](../../build/reference/qspectre.md): genera instrucciones para mitigar determinadas vulnerabilidades de seguridad Spectre.

- [/ Qvec-report (nivel de información de Vectorizador automático)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): permite niveles de informe para la vectorización automática.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
