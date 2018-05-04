---
title: ¿Cuándo es necesario llamar a AtlAxWinTerm? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinTerm
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61830023d3fb67d331784769f32cda4eee8355b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>¿Cuándo es necesario llamar a AtlAxWinTerm?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) anula el registro de la **"AtlAxWin80"** clase de ventana. Debería llamar a esta función (si ya no tiene que crear ventanas host) después de que se hayan destruido todas las ventanas de host existente. Si no llama a esta función, la clase de ventana será anular el registro automáticamente cuando finaliza el proceso.  
  
## <a name="see-also"></a>Vea también  
 Cuando es necesario llamar a AtlAxWinInit  
[Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)

