---
title: Compilador advertencia (nivel 1) C4951 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8317491a1649741c3322af3125fef80c0fb52f47
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4951"></a>Advertencia del compilador (nivel 1) C4951
'function' se ha editado desde que se recopilaron los datos de perfil; los datos de perfil de la función no se han utilizado  
  
 Una función se ha editado en un módulo de entrada a [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de modo que los datos del perfil no están válidos. El módulo de entrada se ha vuelto a compilar después de **/LTCG:PGINSTRUMENT** y tiene una función (***function***) con un flujo de control diferente que el del módulo en el momento de la operación **/LTCG:PGINSTRUMENT** .  
  
 Esta advertencia es informativa. Para solucionar esta advertencia, ejecute **/LTCG:PGINSTRUMENT**, rehaga todas las ejecuciones de prueba y ejecute **/LTCG:PGOPTIMIZE**.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado **/LTCG:PGOPTIMIZE** .
