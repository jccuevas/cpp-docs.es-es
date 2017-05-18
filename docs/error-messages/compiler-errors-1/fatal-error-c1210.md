---
title: Error grave C1210 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1210
dev_langs:
- C++
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
caps.latest.revision: 7
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: f3abd56aebdf7e83bbab10b6083ad6fc14987fbd
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="fatal-error-c1210"></a>Error irrecuperable C1210
La versión del runtime instalada no admite /clr:pure ni /clr:safe  
  
 El **/CLR: pure** y **/CLR: safe** opciones del compilador están desusadas en Visual Studio 2015.  
  
 El error C1210 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.  
  
 Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.  
  
 Para solucionar el error C1210, instale la versión de Common Language Runtime pensada para su uso con el compilador.
