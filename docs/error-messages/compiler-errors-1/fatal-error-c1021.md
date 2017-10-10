---
title: Error irrecuperable C1021 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1021
dev_langs:
- C++
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: aa56ca51293bd5afd6baeeabe11b21159ce8b98e
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1021"></a>Error irrecuperable C1021
comando de preprocesador 'string' no válido  
  
 `string` no es una [directiva de preprocesador](../../preprocessor/preprocessor-directives.md)válida. Para resolver el error, use un nombre de preprocesador válido para `string`.  
  
 El ejemplo siguiente genera la advertencia C1021:  
  
```  
// C1021.cpp  
#BadPreProcName    // C1021 delete line  
```
