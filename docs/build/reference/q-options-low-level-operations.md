---
title: /Q (Opciones) (Operaciones de bajo nivel)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: a6dcbd256fa3510955884d3adba4855b23cdbfab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514262"
---
# <a name="q-options-low-level-operations"></a>/Q (Opciones) (Operaciones de bajo nivel)

Puede usar el **/Q** opciones del compilador para realizar las siguientes operaciones de compilador de bajo nivel:

- [/ Qfast_transcendentals (Force funciones transcendentales rápidas)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): genera funciones transcendentales rápidas.

- [/QIfist (suprimir _ftol)](../../build/reference/qifist-suppress-ftol.md): suprime `_ftol` cuando una conversión de un tipo de punto flotante a un tipo entero es necesario (solo x86).

- [/ Qimprecise_fwaits (quitar comandos fwait en los bloques Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): quita `fwait` comandos dentro de `try` bloques.

- [/Qpar (Paralelizador)](../../build/reference/qpar-auto-parallelizer.md): habilita la paralelización automática de bucles marcados con el [#pragma loop()](../../preprocessor/loop.md) directiva.

- [/ Qpar-report (nivel de información de Paralelizador automático)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): habilita los niveles de ejecución en paralelo automática de informe.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): suprime las optimizaciones de carga de registro de punto flotante y para los movimientos entre memoria y MMX registra.

- [/Qspectre](../../build/reference/qspectre.md): genera instrucciones para mitigar determinadas vulnerabilidades de seguridad de Spectre.

- [/ Qvec-report (nivel de información de Vectorizador automático)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): habilita los niveles para la vectorización automática de informe.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
