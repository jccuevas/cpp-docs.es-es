---
title: Error irrecuperable C1210 | Documentos de Microsoft
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0756ef40282f9a9bffb21788ea1b396600e50362
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1210"></a>Error irrecuperable C1210
La versión del runtime instalada no admite /clr:pure ni /clr:safe  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 El error C1210 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.  
  
 Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.  
  
 Para solucionar el error C1210, instale la versión de Common Language Runtime pensada para su uso con el compilador.
