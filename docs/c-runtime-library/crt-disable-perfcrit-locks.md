---
title: _CRT_DISABLE_PERFCRIT_LOCKS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
dev_langs:
- C++
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 128403009595d85e44007d79c9110b5df530b45e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386662"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS
Deshabilita el bloqueo crítico para el rendimiento en las operaciones de E/S.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#define _CRT_DISABLE_PERFCRIT_LOCKS  
```  
  
## <a name="remarks"></a>Comentarios  
 La definición de este símbolo puede mejorar el rendimiento de programas enlazados a E/S uniproceso al forzar a todas las operaciones de E/S a asumir un modelo de E/S uniproceso. Para más información, vea [Rendimiento de bibliotecas multiproceso](../c-runtime-library/multithreaded-libraries-performance.md).  
  
## <a name="see-also"></a>Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)