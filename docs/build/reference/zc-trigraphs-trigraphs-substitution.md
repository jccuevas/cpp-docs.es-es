---
title: "-Zc: trigraphs (sustitución de trígrafos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 739e772c87c937a552e07a32fa5bb80b1a1e2508
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Sustitución de trígrafos)
Cuando **/Zc: trigraphs** se especifica, el compilador reemplaza una secuencia de caracteres de trígrafo utilizando un carácter de puntuación correspondiente. Para desactivar la sustitución de trígrafos, especifique **/Zc:trigraphs-**. De forma predeterminada, **/Zc: trigraphs** está desactivada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zc:trigraphs[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 Un trígrafo se compone de dos signos de interrogación consecutivos ("??") seguidos de un tercer carácter único. ¿Por ejemplo, el compilador reemplaza el "? = "trígrafos mediante el carácter '#'. Use trígrafos en archivos de código fuente C que usen un juego de caracteres que no contenga representaciones gráficas adecuadas para algunos caracteres de puntuación.  
  
 Para obtener una lista de los trígrafos C/C++ y un ejemplo que muestra cómo usar trígrafos, vea [trígrafos](../../c-language/trigraphs.md).  
  
## <a name="see-also"></a>Vea también  
 [/Zc (ajuste)](../../build/reference/zc-conformance.md)   
 [Trígrafos](../../c-language/trigraphs.md)