---
title: 2.8 enlace de directivas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a70dbc0306005473d427015e81d8b93e895da9fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="28-directive-binding"></a>2.8 Enlace de directivas
Enlace dinámico de directivas debe cumplir las reglas siguientes:  
  
-   El **para**, **secciones**, **único**, **maestro**, y **barrera** directivas enlazar a la dinámicamente envolvente **paralelo**, si existe alguno, independientemente del valor de cualquier **si** cláusula que puede estar presente en dicha directiva. Si actualmente no se está ejecutando ninguna región paralela, las directivas se ejecutan por un equipo que se compone del subproceso principal.  
  
-   El **ordenados** directiva enlaza a dinámicamente envolvente **para**.  
  
-   El **atómica** Directiva exige acceso exclusivo con respecto a **atómica** directivas en todos los subprocesos, no solo el equipo actual.  
  
-   El **crítico** Directiva exige acceso exclusivo con respecto a **crítico** directivas en todos los subprocesos, no solo el equipo actual.  
  
-   Una directiva nunca puede enlazar a cualquier directiva fuera lo más parecido posible dinámicamente envolvente **paralelo**.