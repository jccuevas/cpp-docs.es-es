---
title: Varargs | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7b71cd426bc89570f9d394f3e38dc7a002f6e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380513"
---
# <a name="varargs"></a>Varargs
Si se pasan parámetros a través de varargs (por ejemplo, los argumentos de puntos suspensivos), esencialmente el parámetro normal pasar aplica incluyendo los argumentos quinto y posteriores. Nuevo es responsabilidad del destinatario volcar los argumentos que tomarse la dirección. Para valores de punto flotante, el entero y el registro de punto flotante contendrá el valor flotante en caso de que el destinatario espera el valor en los registros de enteros.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)