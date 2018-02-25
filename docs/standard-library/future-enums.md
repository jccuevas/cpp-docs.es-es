---
title: '&lt;future&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: eebca67270d208f1e8aa233ece80818bdc40f7f1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; (Enumeraciones)
||||  
|-|-|-|  
|[future_errc](#future_errc)|[future_status](#future_status)|[launch](#launch)|  
  
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



