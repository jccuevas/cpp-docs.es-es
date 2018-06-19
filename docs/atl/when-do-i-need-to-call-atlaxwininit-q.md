---
title: ¿Cuándo es necesario llamar a AtlAxWinInit? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinInit
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9aa1dd14ccae555d4ab9acbbac15e9b66cafe6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360278"
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>¿Cuándo es necesario llamar a AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registra el **"AtlAxWin80"** clase de ventana (junto con un par de mensajes de ventana personalizados), por lo que esta función se debe llamar antes de intentar crear una ventana host. Sin embargo, no siempre es necesario llamar a esta función de forma explícita, desde el que hospeda las API (y las clases que las utilizan) a menudo llaman a esta función para usted. No hay peligro en más de una vez al llamar a esta función. .  
  
## <a name="see-also"></a>Vea también  
 Cuando es necesario llamar a AtlAxWinTerm     
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)
