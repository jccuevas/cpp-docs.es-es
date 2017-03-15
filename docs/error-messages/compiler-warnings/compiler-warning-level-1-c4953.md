---
title: Compilador advertencia (nivel 1) C4953 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: be8e32bd07da47d79e974d979eb19466c5b19416
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4953"></a>Advertencia del compilador (nivel 1) C4953
La inclusión en líneas de 'function' se ha editado desde que los datos de perfil se recopilaron; datos de perfil no utilizados  
  
 Al usar [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después `/LTCG:PGINSTRUMENT` y tiene una función (***función***) que editó y donde se ejecuta la prueba existente identifica la función como un candidato para la inclusión entre líneas. Sin embargo, como resultado de volver a compilar el módulo, la función ya no será candidata para la inclusión en líneas.  
  
 Esta advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .
