---
title: "signal (Constantes de acción) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs:
- C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: f316218673d83187f29934ebd75a838b31005912
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="signal-action-constants"></a>signal (Constantes de acción)
La acción realizada cuando se recibe la señal de interrupción depende del valor de `func`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento `func` debe ser una dirección de función o una de las constantes de manifiesto enumeradas a continuación y definidas en SIGNAL.H.  
  
 `SIG_DFL`  
 Usa la respuesta predeterminada del sistema. Si el programa de llamada usa E/S de secuencia, no se vacían los búferes creados por la biblioteca en tiempo de ejecución.  
  
 `SIG_IGN`  
 Ignora la señal de interrupción. Este valor nunca debe proporcionarse para `SIGFPE`, ya que el estado de punto flotante del proceso se deja sin definir.  
  
 `SIG_SGE`  
 Indica un error ocurrido en la señal.  
  
 `SIG_ACK`  
 Indica que se ha recibido una confirmación.  
  
 `SIG_ERR`  
 Una señal ha producido un tipo de error devuelto que indica que se ha producido un error.  
  
## <a name="see-also"></a>Vea también  
 [signal](../c-runtime-library/reference/signal.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)
