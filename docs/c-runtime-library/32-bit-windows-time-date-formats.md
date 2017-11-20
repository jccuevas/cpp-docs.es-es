---
title: Formatos de fecha y hora de Windows de 32 bits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.time
dev_langs: C++
helpviewer_keywords: 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23f56a9ef86a33b99f1014cb2cf18a92bdfbd753
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="32-bit-windows-timedate-formats"></a>Formatos de fecha y hora de Windows de 32 bits
La fecha y la hora del archivo se almacenan de manera individual, con enteros sin signo como campos de bits. La fecha y la hora del archivo se empaquetan de la manera siguiente:  
  
### <a name="time"></a>Hora  
  
|Posición de bit:|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|  
|-------------------|-----------------------|---------------------------|-----------------------|  
|Longitud:|5|6|5|  
|Contenido:|horas|minutos|Incrementos de 2 segundos|  
|Intervalo de valores:|0-23|0-59|0-29 en intervalos de 2 segundos|  
  
### <a name="date"></a>Fecha  
  
|Posición de bit:|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|  
|-------------------|-------------------------------|-------------------|-----------------------|  
|Longitud:|7|4|5|  
|Contenido:|año|mes|día|  
|Intervalo de valores:|0-119|1-12|1-31|  
||(con respecto a 1980)|||  
  
## <a name="see-also"></a>Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)