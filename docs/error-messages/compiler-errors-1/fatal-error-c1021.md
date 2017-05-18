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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: b1ea205d21b0d73f269ff475f9224ab2c10ee562
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1021"></a>Error irrecuperable C1021
comando de preprocesador 'string' no válido  
  
 `string`no es válido [directiva de preprocesador](../../preprocessor/preprocessor-directives.md). Para resolver el error, use un nombre de preprocesador válido para `string`.  
  
 El ejemplo siguiente genera la advertencia C1021:  
  
```  
// C1021.cpp  
#BadPreProcName    // C1021 delete line  
```
