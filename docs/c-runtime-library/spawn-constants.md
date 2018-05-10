---
title: spawn (Constantes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
dev_langs:
- C++
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3a069f9f29f6fd15c3ce21111a37757519af229
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="spawn-constants"></a>spawn (Constantes)
## <a name="syntax"></a>Sintaxis  
  
```  
#include <process.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento `mode` determina la acción que realiza el proceso de llamada antes y durante una operación spawn. A continuación se indican valores posibles de `mode`:  
  
|Constante|Significado|  
|--------------|-------------|  
|`_P_OVERLAY`|Superpone el nuevo proceso al proceso de llamada, lo que destruye el proceso de llamada (mismo efecto que las llamadas `_exec`).|  
|`_P_WAIT`|Suspende el subproceso de llamada hasta que se completa la ejecución del proceso nuevo (`_spawn` sincrónica).|  
|`_P_NOWAIT`, `_P_NOWAITO`|Continúa ejecutando el proceso de llamada al mismo tiempo que el nuevo proceso (`_spawn` asincrónica).|  
|`_P_DETACH`|Continúa ejecutando el proceso de llamada; el nuevo proceso se ejecuta en segundo plano sin acceso a la consola ni al teclado. Las llamadas a `_cwait` en el nuevo proceso producirán un error. Se trata de una función `_spawn` asincrónica.|  
  
## <a name="see-also"></a>Vea también  
 [_spawn, _wspawn (Funciones)](../c-runtime-library/spawn-wspawn-functions.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)