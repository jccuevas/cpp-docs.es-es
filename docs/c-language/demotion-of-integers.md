---
title: Disminución de enteros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d380fd36cc71b6d188bbbfe8e51ce3185405611
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381725"
---
# <a name="demotion-of-integers"></a>Disminución de enteros
**ANSI 3.2.1.2** El resultado de convertir un entero en un entero menor con signo o el resultado de convertir un entero sin signo en un entero con signo de igual longitud, si no se puede representar el valor  
  
 Cuando un entero **long** se convierte en un entero **short**, o cuando un entero **short** se convierte en un `char`, se conservan los bytes menos significativos.  
  
 Por ejemplo, esta línea  
  
```  
short x = (short)0x12345678L;  
```  
  
 asigna el valor 0x5678 a `x`, y esta línea  
  
```  
char y = (char)0x1234;  
```  
  
 asigna el valor 0x34 a `y`.  
  
 Cuando las variables con signo se convierten en variables sin signo, y viceversa, los patrones de bits permanecen iguales. Por ejemplo, la conversión de -2 (0xFE) en un valor sin signo produce 254 (también 0xFE).  
  
## <a name="see-also"></a>Vea también  
 [Enteros](../c-language/integers.md)