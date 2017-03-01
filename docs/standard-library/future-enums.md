---
title: '&lt;future&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b1f8c56de97789bea4f0923cd87e8144382e1ed0
ms.lasthandoff: 02/24/2017

---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; (Enumeraciones)
||||  
|-|-|-|  
|[future_errc (Enumeración)](#future_errc_enumeration)|[future_status (Enumeración)](#future_status_enumeration)|[launch (Enumeración)](#launch_enumeration)|  
  
##  <a name="a-namefutureerrcenumerationa--futureerrc-enumeration"></a><a name="future_errc_enumeration"></a>  future_errc (Enumeración)  
 Proporciona nombres simbólicos para todos los errores notificados por la clase [future_error](../standard-library/future-error-class.md).  
  
class future_errc { broken_promise, future_already_retrieved, promise_already_satisfied, no_state };  
  
##  <a name="a-namefuturestatusenumerationa--futurestatus-enumeration"></a><a name="future_status_enumeration"></a>  future_status (Enumeración)  
 Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.  
  
```
enum future_status{    ready,
    timeout,
 deferred};
```  
  
##  <a name="a-namelaunchenumerationa--launch-enumeration"></a><a name="launch_enumeration"></a>  launch (Enumeración)  
 Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla [async](../standard-library/future-functions.md#async_function).  
  
class launch{ async, deferred };  
  
## <a name="see-also"></a>Vea también  
 [\<future>](../standard-library/future.md)




