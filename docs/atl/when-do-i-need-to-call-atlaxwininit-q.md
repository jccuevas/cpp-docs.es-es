---
title: "¿Cuándo es necesario llamar a AtlAxWinInit? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AtlAxWinInit
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69dfcfbe0c8c05d275a5f3a8f86c30b0e59bd3a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>¿Cuándo es necesario llamar a AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registra el **"AtlAxWin80"** clase de ventana (junto con un par de mensajes de ventana personalizados), por lo que esta función se debe llamar antes de intentar crear una ventana host. Sin embargo, no siempre es necesario llamar a esta función de forma explícita, desde el que hospeda las API (y las clases que las utilizan) a menudo llaman a esta función para usted. No hay peligro en más de una vez al llamar a esta función. .  
  
## <a name="see-also"></a>Vea también  
 Cuando es necesario llamar a AtlAxWinTerm     
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)
