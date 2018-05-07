---
title: C4746 de advertencia del compilador | Documentos de Microsoft
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
ms.openlocfilehash: 9d00c75b2b7cdf2fdafb4e109496a701fb561cb9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4746"></a>C4746 de advertencia del compilador
acceso volátil de '\<expresión >' está sujeta a /volatile: [iso&#124;ms] establecer; considere el uso de funciones intrínsecas de __iso_volatile_load/almacén.  
  
 C4746 se genera cada vez que se tiene acceso directamente a una variable volátil. Está diseñado para ayudar a los desarrolladores a identificar ubicaciones del código que se ven afectados por el modelo volátil específico que se especifica actualmente (que puede controlarse con el [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) opción del compilador). En concreto, puede ser útil para localizar las barreras de memoria de hardware generados por el compilador cuando se utiliza /volatile:ms.  
  
 El __iso_volatile_load/intrínsecos de almacén pueden utilizarse para un acceso explícito a memoria volátil sin que se vean afectados por el modelo volátil. Uso de estas funciones intrínsecas, no se desencadenará C4746.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.