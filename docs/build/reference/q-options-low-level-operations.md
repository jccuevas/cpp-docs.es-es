---
title: Opciones -Q (operaciones de bajo nivel) | Microsoft Docs
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
ms.openlocfilehash: 15854333a9f26f87d20f7819327e68050ab37bf6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717797"
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
