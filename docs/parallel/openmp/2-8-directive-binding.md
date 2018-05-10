---
title: 2.8 enlace de directivas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02492b228b4bb47a800955f078a59ce680312a87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="28-directive-binding"></a>2.8 Enlace de directivas
Enlace dinámico de directivas debe cumplir las reglas siguientes:  
  
-   El **para**, **secciones**, **único**, **maestro**, y **barrera** directivas enlazar a la dinámicamente envolvente **paralelo**, si existe alguno, independientemente del valor de cualquier **si** cláusula que puede estar presente en dicha directiva. Si actualmente no se está ejecutando ninguna región paralela, las directivas se ejecutan por un equipo que se compone del subproceso principal.  
  
-   El **ordenados** directiva enlaza a dinámicamente envolvente **para**.  
  
-   El **atómica** Directiva exige acceso exclusivo con respecto a **atómica** directivas en todos los subprocesos, no solo el equipo actual.  
  
-   El **crítico** Directiva exige acceso exclusivo con respecto a **crítico** directivas en todos los subprocesos, no solo el equipo actual.  
  
-   Una directiva nunca puede enlazar a cualquier directiva fuera lo más parecido posible dinámicamente envolvente **paralelo**.