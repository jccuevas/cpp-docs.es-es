---
title: setjmp longjump | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 744b855d1b867507b54973f17e2a4f98b63e2b67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="setjmplongjump"></a>setjmp/longjump
Cuando se incluye setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) dará como resultado un desenredo que invoca a los destructores y finalmente llama.  Esto difiere de x86, donde incluir resultados de setjmp.h en cláusulas finally y destructores no que se va a invocar.  
  
 Una llamada a `setjmp` conserva el puntero de pila actual, los registros no volátiles y los registros de MxCsr.  Las llamadas a `longjmp` vuelva a la última `setjmp` llamar a sitio y restablece el puntero de pila, registros no volátiles y MxCsr registra, al estado mantenido desde la última `setjmp` llamar.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)