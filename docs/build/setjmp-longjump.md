---
title: setjmp longjump | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3617f70e7c62e1845d8d24e11cebdd7738c507f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setjmplongjump"></a>setjmp/longjump
Cuando se incluye setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) dará como resultado un desenredo que invoca a los destructores y finalmente llama.  Esto difiere de x86, donde incluir resultados de setjmp.h en cláusulas finally y destructores no que se va a invocar.  
  
 Una llamada a `setjmp` conserva el puntero de pila actual, los registros no volátiles y los registros de MxCsr.  Las llamadas a `longjmp` vuelva a la última `setjmp` llamar a sitio y restablece el puntero de pila, registros no volátiles y MxCsr registra, al estado mantenido desde la última `setjmp` llamar.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)