---
title: /Q (Opciones) (Operaciones de bajo nivel)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 5bbb63b4f437f8aefd5c84c1c1c4bd20bdb965cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319400"
---
# <a name="q-options-low-level-operations"></a>/Q (Opciones) (Operaciones de bajo nivel)

Puede usar el **/Q** opciones del compilador para realizar las siguientes operaciones de compilador de bajo nivel:

- [/ Qfast_transcendentals (Force funciones transcendentales rápidas)](qfast-transcendentals-force-fast-transcendentals.md): Genera funciones transcendentales rápidas.

- [/QIfist (Suppress _ftol)](qifist-suppress-ftol.md): Suprime `_ftol` cuando una conversión de un tipo de punto flotante a un tipo entero es necesario (solo x86).

- [/ Qimprecise_fwaits (quitar comandos fwait en los bloques Try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Quita los comandos `fwait` del interior de los bloques `try` .

- [/Qpar (Paralelizador)](qpar-auto-parallelizer.md): Habilita la ejecución en paralelo automática de bucles marcados con la directiva [#pragma loop()](../../preprocessor/loop.md) .

- [/ Qpar-report (Paralelizador automático nivel)](qpar-report-auto-parallelizer-reporting-level.md): Habilita los niveles de informe para la ejecución en paralelo automática.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Suprime las optimizaciones para las cargas de registro de punto flotante y para los movimientos entre la memoria y los registros MMX.

- [/Qspectre](qspectre.md): Genera instrucciones para mitigar determinadas vulnerabilidades de seguridad de Spectre.

- [/ Qvec-report (Vectorizador automático nivel)](qvec-report-auto-vectorizer-reporting-level.md): Habilita los niveles de informe para la vectorización automática.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
