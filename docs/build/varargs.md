---
title: Varargs | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3d22a5c3f20480d1e904ec8e087114385ba7ee9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="varargs"></a>Varargs
Si se pasan parámetros a través de varargs (por ejemplo, los argumentos de puntos suspensivos), esencialmente el parámetro normal pasar aplica incluyendo los argumentos quinto y posteriores. Nuevo es responsabilidad del destinatario volcar los argumentos que tomarse la dirección. Para valores de punto flotante, el entero y el registro de punto flotante contendrá el valor flotante en caso de que el destinatario espera el valor en los registros de enteros.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)