---
title: "Conversiones de llamada de función | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc3d425e3f9273dfc3ad1517aa441920057d70d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="function-call-conversions"></a>Conversiones de llamada de función
El tipo de conversión que se realiza en los argumentos de una llamada a función depende de la presencia de un prototipo de función (declaración adelantada) con tipos de argumento declarados para la función llamada.  
  
 Si un prototipo de función está presente e incluye tipos de argumento declarados, el compilador realiza la comprobación de tipos (vea [Funciones](../c-language/functions-c.md)).  
  
 Si no hay ningún prototipo de función, solo se realizan las conversiones aritméticas habituales en los argumentos de la llamada a función. Estas conversiones se realizan independientemente en cada argumento de la llamada. Esto significa que un valor **float** se convierte en **double**, un valor `char` o **short** se convierte en `int`, y `unsigned char` o **unsigned short** se convierte en `unsigned int`.  
  
## <a name="see-also"></a>Vea también  
 [Conversiones de tipos](../c-language/type-conversions-c.md)