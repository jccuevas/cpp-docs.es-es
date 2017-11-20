---
title: Error del compilador C3537 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3537
dev_langs: C++
helpviewer_keywords: C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f425ee0d93a277bac5dc1f0a798c1a7cc3ed3bac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3537"></a>Error del compilador C3537
'type': no se puede convertir a un tipo que contiene 'auto'  
  
 No se puede convertir una variable para el tipo indicado porque contiene el tipo de la `auto` palabra clave y el valor predeterminado [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) opción del compilador está en vigor.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente genera el error C3537 porque las variables se convierten a un tipo que contiene el `auto` palabra clave.  
  
```  
// C3537.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int value = 123;  
   auto(value);                        // C3537  
   (auto)value;                        // C3537  
   auto x1 = auto(value);              // C3537  
   auto x2 = (auto)value;              // C3537  
   auto x3 = static_cast<auto>(value); // C3537  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)