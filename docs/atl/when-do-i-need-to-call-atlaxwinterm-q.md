---
title: "¿Cuándo es necesario llamar a AtlAxWinTerm? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinTerm
dev_langs: C++
helpviewer_keywords: AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cdba5255560f220a80a016f17e574721b12f486d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>¿Cuándo es necesario llamar a AtlAxWinTerm?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) anula el registro de la **"AtlAxWin80"** clase de ventana. Debería llamar a esta función (si ya no tiene que crear ventanas host) después de que se hayan destruido todas las ventanas de host existente. Si no llama a esta función, la clase de ventana será anular el registro automáticamente cuando finaliza el proceso.  
  
## <a name="see-also"></a>Vea también  
 Cuando es necesario llamar a AtlAxWinInit  
[Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)

