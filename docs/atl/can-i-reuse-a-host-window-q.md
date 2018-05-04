---
title: ¿Puedo volver a usar una ventana Host? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- host windows
ms.assetid: bcd08ab1-cfcf-49e3-b4e8-ac134d141005
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8a108c8c4e9b515a75399f82e333b00a5210e8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="can-i-reuse-a-host-window"></a>¿Puedo volver a usar una ventana Host?
No se recomienda que vuelva a utilizar windows de host. Para garantizar la solidez del código, se debe asociar la duración de la ventana del host a la duración de un control único.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)

