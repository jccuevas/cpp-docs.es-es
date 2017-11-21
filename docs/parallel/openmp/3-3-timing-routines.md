---
title: 3.3 rutinas temporales | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 285102b27a290d693372e414645a41f5b5de1834
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="33-timing-routines"></a>3.3 Rutinas temporales
Las funciones descritas en esta sección admiten un temporizador de reloj portátil:  
  
-   El `omp_get_wtime` función devuelve la hora de reloj transcurrido.  
  
-   El `omp_get_wtick` función devuelve segundos entre ciclos de reloj sucesivas.