---
title: /Q (Opciones) (Operaciones de bajo nivel)
ms.date: 01/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 6348226aa38d1f2eefdf9e19e27c4c87bd2f0812
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927668"
---
# <a name="q-options-low-level-operations"></a>/Q (Opciones) (Operaciones de bajo nivel)

Puede usar las opciones del compilador **/q** para realizar las siguientes operaciones de compilador de bajo nivel:

- [/Qfast_transcendentals (Force Fast funciones transcendentales)](qfast-transcendentals-force-fast-transcendentals.md): Genera funciones transcendentales rápidas.

- [/QIfist (Suppress _ftol)](qifist-suppress-ftol.md): Suprime `_ftol` cuando se requiere una conversión de un tipo de punto flotante a un tipo entero (solo x86).

- [/Qimprecise_fwaits (quitar comandos fwait dentro de los bloques try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Quita los comandos `fwait` del interior de los bloques `try` .

- [/QPAR (paralelizador automático)](qpar-auto-parallelizer.md): Habilita la ejecución en paralelo automática de bucles marcados con la directiva [#pragma loop()](../../preprocessor/loop.md) .

- [/QPAR-Report (nivel de informe de paralelizador automático automática)](qpar-report-auto-parallelizer-reporting-level.md): Habilita los niveles de informe para la ejecución en paralelo automática.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Suprime las optimizaciones para las cargas de registros de punto flotante y para los movimientos entre la memoria y los registros MMX.

- [/Qspectre](qspectre.md): Genera instrucciones para mitigar ciertas vulnerabilidades de seguridad de Spectre.

- [/Qvec-Report (nivel de informe de vectorizador automático automática)](qvec-report-auto-vectorizer-reporting-level.md): Habilita los niveles de informe para la vectorización automática.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
