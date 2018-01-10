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
ms.workload: cplusplus
ms.openlocfilehash: ecea42172ed285f24a22cba004fb156784483643
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="underflow-of-floating-point-values"></a>Subdesbordamiento de valores de punto flotante
**ANSI 4.5.1** Si las funciones matemáticas establecen la expresión de entero `errno` en el valor de la macro `ERANGE` en errores de intervalo de subdesbordamiento  
  
 Un subdesbordamiento de punto flotante no establece la expresión `errno` en `ERANGE`. Cuando un valor se aproxima a cero y finalmente sufre subdesbordamiento, el valor se establece en cero.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)