---
title: Error irrecuperable C1045 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1045
dev_langs:
- C++
helpviewer_keywords:
- C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 523c717f2e3e3e7485cfbd1f4c2e7bf270b4e6a3
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1045"></a>Error irrecuperable C1045
límite del compilador : las especificaciones de vinculación están demasiado anidadas  
  
 Los externos anidados superan el límite del compilador. Se permiten los externos anidados con el tipo de vinculación externa, como `extern` "C++". Reduzca el número de externos anidados para resolver el error.
