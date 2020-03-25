---
title: Error del compilador C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: a0cdd528eca8ea267c62e6d44752d29ae16830c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205626"
---
# <a name="compiler-error-c2415"></a>Error del compilador C2415

tipo de operando incorrecto

El código de operación no utiliza los operandos de este tipo.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El código de operación no admite el número de operandos utilizado. Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.

1. Un procesador más reciente admite la instrucción con tipos adicionales. Ajuste la opción [/Arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md) para usar el procesador posterior.
