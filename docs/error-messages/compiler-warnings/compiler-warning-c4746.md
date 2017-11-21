---
title: C4746 de advertencia del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b88f51aa9365c0795c8d3d944ba9f3a8db059d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4746"></a>C4746 de advertencia del compilador
acceso volátil de '\<expresión >' está sujeta a /volatile: [iso &#124; ms] establecer; considere el uso de funciones intrínsecas de __iso_volatile_load/almacén.  
  
 C4746 se genera cada vez que se tiene acceso directamente a una variable volátil. Está diseñado para ayudar a los desarrolladores a identificar ubicaciones del código que se ven afectados por el modelo volátil específico que se especifica actualmente (que puede controlarse con el [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) opción del compilador). En concreto, puede ser útil para localizar las barreras de memoria de hardware generados por el compilador cuando se utiliza /volatile:ms.  
  
 El __iso_volatile_load/intrínsecos de almacén pueden utilizarse para un acceso explícito a memoria volátil sin que se vean afectados por el modelo volátil. Uso de estas funciones intrínsecas, no se desencadenará C4746.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.