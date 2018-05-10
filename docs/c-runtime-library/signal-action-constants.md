---
title: signal (Constantes de acción) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b6f645d474e697bf662a5dd63973dd54c329eb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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