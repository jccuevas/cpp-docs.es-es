---
title: "¿Cuándo es necesario llamar a AtlAxWinInit? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinInit
dev_langs: C++
helpviewer_keywords: AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ec7d8d15b8219071b593368ed539d92ff3c9032
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>¿Cuándo es necesario llamar a AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registra el **"AtlAxWin80"** clase de ventana (junto con un par de mensajes de ventana personalizados), por lo que esta función se debe llamar antes de intentar crear una ventana host. Sin embargo, no siempre es necesario llamar a esta función de forma explícita, desde el que hospeda las API (y las clases que las utilizan) a menudo llaman a esta función para usted. No hay peligro en más de una vez al llamar a esta función. .  
  
## <a name="see-also"></a>Vea también  
 Cuando es necesario llamar a AtlAxWinTerm     
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)
