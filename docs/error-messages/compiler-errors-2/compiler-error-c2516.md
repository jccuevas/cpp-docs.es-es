---
title: Error del compilador C2516 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2516
dev_langs: C++
helpviewer_keywords: C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4d0e25a0c9e61a82d8d6bccec8d2501df1671ec2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2516"></a>Error del compilador C2516
'name': no es una clase base válida  
  
 La clase se deriva de un nombre de tipo definido por un `typedef` instrucción.  
  
 El ejemplo siguiente genera C2516:  
  
```  
// C2516.cpp  
typedef unsigned long ulong;  
class C : public ulong {}; // C2516  
```