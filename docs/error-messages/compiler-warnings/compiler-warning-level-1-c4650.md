---
title: Del compilador (nivel 1) de la advertencia C4650 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d49b21452465f26d6e696f928c04c20dc0e33307
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052901"
---
# <a name="compiler-warning-level-1-c4650"></a>Advertencia del compilador (nivel 1) C4650

información de depuración no está en el encabezado precompilado; solo símbolos globales del encabezado estará disponibles

No se compiló el archivo de encabezado precompilado con información de depuración simbólica de Microsoft.

Cuando vincula, el archivo de biblioteca de vínculos dinámicos o ejecutable resultante no incluirá información de depuración para los símbolos locales contenidos en el encabezado precompilado.

Esta advertencia puede evitarse volviendo a compilar el archivo de encabezado precompilado con la [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción de línea de comandos.