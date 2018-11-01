---
title: Advertencia del compilador C4746
ms.date: 11/04/2016
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 1b79eed2134b8c6310e508e56b3388c6f38fe4b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625893"
---
# <a name="compiler-warning-c4746"></a>Advertencia del compilador C4746

acceso volátil de '\<expresión >' está sujeta a /volatile: [iso&#124;ms]; considere el uso de funciones intrínsecas __iso_volatile_load/store.

C4746 se genera cada vez que se tiene acceso directamente a una variable volátil. Se pretende ayudar a los desarrolladores a identificar las ubicaciones de código que se ven afectadas por el modelo volátil específico está especificado actualmente (que se puede controlar con el [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) opción del compilador). En concreto, puede ser útil para localizar las barreras de memoria de hardware generados por el compilador cuando se usa/volatile: MS.

Las funciones intrínsecas __iso_volatile_load/store pueden utilizarse para obtener explícitamente acceso a memoria volátil sin que se vean afectados por el modelo volátil. Estas funciones intrínsecas no desencadenará C4746.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.