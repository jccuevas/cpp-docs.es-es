---
title: Advertencia del compilador (nivel 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199573"
---
# <a name="compiler-warning-level-1-c4650"></a>Advertencia del compilador (nivel 1) C4650

la información de depuración no está en el encabezado precompilado; solo estarán disponibles los símbolos globales del encabezado

No se compiló el archivo de encabezado precompilado con información de depuración simbólica de Microsoft.

Cuando se vincula, el archivo ejecutable o de biblioteca de vínculos dinámicos resultante no incluirá información de depuración para los símbolos locales contenidos en el encabezado precompilado.

Esta advertencia se puede evitar volviendo a compilar el archivo de encabezado precompilado con la opción de línea de comandos [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .
