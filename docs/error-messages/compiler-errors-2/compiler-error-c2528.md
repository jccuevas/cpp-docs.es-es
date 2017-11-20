---
title: Error del compilador C2528 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2528
dev_langs: C++
helpviewer_keywords: C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: df8179dbf51f329d12420593f187aad37d76564e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2528"></a>Error del compilador C2528
'name': puntero a referencia no es válido  
  
 No se puede declarar un puntero a una referencia. Desreferenciación de la variable antes de declarar un puntero a ella.  
  
 El ejemplo siguiente genera C2528:  
  
```  
// C2528.cpp  
int i;  
int &ir = i;  
int & (*irptr) = ir;    // C2528  
```