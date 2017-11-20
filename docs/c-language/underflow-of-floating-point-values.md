---
title: Subdesbordamiento de valores de punto flotante | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f74624f935c9a1384c1c4992004b12c7847e9fd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="underflow-of-floating-point-values"></a>Subdesbordamiento de valores de punto flotante
**ANSI 4.5.1** Si las funciones matemáticas establecen la expresión de entero `errno` en el valor de la macro `ERANGE` en errores de intervalo de subdesbordamiento  
  
 Un subdesbordamiento de punto flotante no establece la expresión `errno` en `ERANGE`. Cuando un valor se aproxima a cero y finalmente sufre subdesbordamiento, el valor se establece en cero.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)