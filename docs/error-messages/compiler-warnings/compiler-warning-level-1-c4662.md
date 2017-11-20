---
title: Compilador advertencia (nivel 1) C4662 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4662
dev_langs: C++
helpviewer_keywords: C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 575d0493b57b5d41e57244bbed4e2ce0899dc274
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4662"></a>Advertencia del compilador (nivel 1) C4662
creación de instancias explícita; la clase de plantilla 'identifier1' no tiene definición a partir de la cual especializar 'identifier2'  
  
 La clase de plantilla especificada se declaró, pero no se definió.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4662.cpp  
// compile with: /W1 /LD  
template<class T, int i> class MyClass; // no definition  
template MyClass< int, 1>;              // C4662  
```