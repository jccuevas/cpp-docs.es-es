---
title: signal (Constantes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs:
- C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 279f4beb3b550f672ac3950c31f3653ca1f00ba2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="signal-constants"></a>signal (Constantes)
## <a name="syntax"></a>Sintaxis  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento `sig` debe ser una de las constantes de manifiesto enumeradas a continuación y definidas en SIGNAL.H.  
  
 `SIGABRT`  
 Terminación anómala. La acción predeterminada finaliza el programa de llamada con el código de salida 3.  
  
 `SIGABRT_COMPAT`  
 Igual que SIGABRT. Por compatibilidad con otras plataformas.  
  
 `SIGFPE`  
 Error de punto flotante, como desbordamiento, división por cero u operación no válida. La acción predeterminada finaliza el programa de llamada.  
  
 `SIGILL`  
 Instrucción no válida. La acción predeterminada finaliza el programa de llamada.  
  
 `SIGINT`  
 Interrupción de CTRL+C. La acción predeterminada finaliza el programa de llamada con el código de salida 3.  
  
 `SIGSEGV`  
 Acceso no válido a almacenamiento. La acción predeterminada finaliza el programa de llamada.  
  
 `SIGTERM`  
 Solicitud de finalización enviada al programa. La acción predeterminada finaliza el programa de llamada con el código de salida 3.  
  
 `SIG_ERR`  
 Una señal ha producido un tipo de error devuelto que indica que se ha producido un error.  
  
## <a name="see-also"></a>Vea también  
 [signal](../c-runtime-library/reference/signal.md)   
 [raise](../c-runtime-library/reference/raise.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)