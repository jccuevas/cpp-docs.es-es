---
title: Compilador advertencia (nivel 1) C4952 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4952
dev_langs: C++
helpviewer_keywords: C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3edf2d7be49375ad4c281bb8ff79c111fe6e15f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4952"></a>Advertencia del compilador (nivel 1) C4952
'función': no se encuentran datos de perfil en la base de datos del programa 'archivo_pgd'  
  
 Al usar [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después `/LTCG:PGINSTRUMENT` y que tiene presente una nueva función (***function***).  
  
 La advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .