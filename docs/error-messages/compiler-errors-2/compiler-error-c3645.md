---
title: Error del compilador C3645 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3645
dev_langs: C++
helpviewer_keywords: C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43bda10ee2e4f2939061d70cfcf19da950909d03
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3645"></a>Error del compilador C3645
'función': no se puede utilizar __clrcall en funciones compiladas para código nativo  
  
 La presencia de algunas palabras clave en una función hará que la función que se va a compilar en código nativo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3645.  
  
```  
// C3645.cpp  
// compile with: /clr /c  
#pragma unmanaged   
int __clrcall dog() {}   // C3645  
```