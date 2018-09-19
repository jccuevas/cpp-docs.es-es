---
title: Advertencia del compilador C4746 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6abce7ebbcdc41effed05ccf54337e3976c34e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054875"
---
# <a name="compiler-warning-c4746"></a>Advertencia del compilador C4746

acceso volátil de '\<expresión >' está sujeta a /volatile: [iso&#124;ms]; considere el uso de funciones intrínsecas __iso_volatile_load/store.

C4746 se genera cada vez que se tiene acceso directamente a una variable volátil. Se pretende ayudar a los desarrolladores a identificar las ubicaciones de código que se ven afectadas por el modelo volátil específico está especificado actualmente (que se puede controlar con el [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) opción del compilador). En concreto, puede ser útil para localizar las barreras de memoria de hardware generados por el compilador cuando se usa/volatile: MS.

Las funciones intrínsecas __iso_volatile_load/store pueden utilizarse para obtener explícitamente acceso a memoria volátil sin que se vean afectados por el modelo volátil. Estas funciones intrínsecas no desencadenará C4746.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.