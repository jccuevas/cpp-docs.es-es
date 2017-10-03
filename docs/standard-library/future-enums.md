---
title: '&lt;future&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 11
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 835abafde46858bd108dfa648a246345bd254eaf
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; (Enumeraciones)
||||  
|-|-|-|  
|[future_errc](#future_errc)|[future_status](#future_status)|[iniciar](#launch)|  
  
##  <a name="future_errc"></a>  future_errc (Enumeración)  
 Proporciona nombres simbólicos para todos los errores notificados por la clase [future_error](../standard-library/future-error-class.md).  
  
class future_errc { broken_promise, future_already_retrieved, promise_already_satisfied, no_state };  
  
##  <a name="future_status"></a>  future_status (Enumeración)  
 Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.  
  
```
enum future_status{    ready,
    timeout,
 deferred};
```  
  
##  <a name="launch"></a>  launch (Enumeración)  
 Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla [async](../standard-library/future-functions.md#async).  
  
class launch{ async, deferred };  
  
## <a name="see-also"></a>Vea también  
 [\<future>](../standard-library/future.md)




