---
title: Subdesbordamiento de valores de punto flotante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ceaa41dcaca88c7857a03c16ccccabdba086fd0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="underflow-of-floating-point-values"></a>Subdesbordamiento de valores de punto flotante
**ANSI 4.5.1** Si las funciones matemáticas establecen la expresión de entero `errno` en el valor de la macro `ERANGE` en errores de intervalo de subdesbordamiento  
  
 Un subdesbordamiento de punto flotante no establece la expresión `errno` en `ERANGE`. Cuando un valor se aproxima a cero y finalmente sufre subdesbordamiento, el valor se establece en cero.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)