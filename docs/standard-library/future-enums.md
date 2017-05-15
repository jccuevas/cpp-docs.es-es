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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 786d999dc03692c11e2c511023f1feb2c84573f8
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

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




