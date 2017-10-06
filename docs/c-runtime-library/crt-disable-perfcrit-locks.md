---
title: _CRT_DISABLE_PERFCRIT_LOCKS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
dev_langs:
- C++
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c88428931b84b996ee711eb17fd42190a2c20e15
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

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
