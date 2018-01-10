---
title: Advertencia A4012 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A4012
dev_langs: C++
helpviewer_keywords: A4012
ms.assetid: 842b1259-9679-4eeb-a02d-672a583a94e5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0648d2bac0d300fc8e2c696b54741a3d7293a4f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ml-warning-a4012"></a>Advertencia A4012 de ML
**información del número de línea de segmento sin que la clase 'CODE'**  
  
 Hay instrucciones de un segmento que no tenía un nombre de clase que termina con "CODE". El ensamblador no genera información de CodeView para estas instrucciones.  
  
 CodeView no puede procesar módulos con código en segmentos con nombres de clase que no terminan con "CODE".  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)