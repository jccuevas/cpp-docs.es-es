---
title: /Q (Opciones) (Operaciones de bajo nivel)
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 722a63a43e5e08fe80b26f908c7ae92df2fdb29c
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034524"
---
# <a name="q-options-low-level-operations"></a>/Q (Opciones) (Operaciones de bajo nivel)

Puede usar las opciones del compilador **/q** para realizar las siguientes operaciones de compilador de bajo nivel:

- [/Qfast_transcendentals (Force Fast funciones transcendentales)](qfast-transcendentals-force-fast-transcendentals.md): genera funciones transcendentales rápido.

- [/QIfist (suprimir _ftol)](qifist-suppress-ftol.md): suprime `_ftol` cuando se requiere una conversión de un tipo de punto flotante a un tipo entero (solo x86).

- [/Qimprecise_fwaits (quitar comandos fwait dentro de los bloques try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): quita `fwait` comandos dentro de `try` bloques.

- [/QIntel-JCC-Erratum](qintel-jcc-erratum.md): reduce el impacto en el rendimiento causado por la actualización de microcódigo de errata de código condicional de Intel (JCC).

- [/QPAR (auto-paralelizador automático)](qpar-auto-parallelizer.md): habilita la paralelización automática de bucles marcados con la Directiva de [bucle #pragma ()](../../preprocessor/loop.md) .

- [/QPAR-Report (nivel de informe de paralelizador automático automática)](qpar-report-auto-parallelizer-reporting-level.md): habilita los niveles de informes para la paralelización automática.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): suprime las optimizaciones para las cargas de registro de punto flotante y para los movimientos entre la memoria y los registros MMX.

- [/Qspectre](qspectre.md): genera instrucciones para mitigar ciertas vulnerabilidades de seguridad de Spectre.

- [/Qspectre-Load](qspectre-load.md): genera instrucciones para mitigar las vulnerabilidades de seguridad de Spectre basadas en cargas.

- [/Qspectre-Load-CF](qspectre-load-cf.md): genera instrucciones para mitigar las vulnerabilidades de seguridad de Spectre en función de las instrucciones de flujo de control que se cargan.

- [/Qvec-Report (vectorizador automático)](qvec-report-auto-vectorizer-reporting-level.md): habilita los niveles de informe para la vectorización automática.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
