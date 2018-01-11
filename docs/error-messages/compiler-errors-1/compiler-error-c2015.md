---
title: Compilador Error C2015 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2015
dev_langs: C++
helpviewer_keywords: C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a04a5c113ca39dac137f2f225a8dcad9318a29bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2015"></a>C2015 de Error del compilador
Hay demasiados caracteres en la constante  
  
 Una constante de caracteres contiene más de dos caracteres. El límite es un carácter para las constantes de caracteres estándar y dos caracteres para las constantes de cadenas largas de caracteres.  
  
 Una secuencia de escape, por ejemplo, \t, se convierte en un único carácter.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2015:  
  
```  
// C2015.cpp  
// compile with: /c  
  
char test1 = 'error';   // C2015  
char test2 = 'e';   // OK  
```  
  
## <a name="example"></a>Ejemplo  
 C2015 también se puede producir cuando se usa una extensión de Microsoft, constantes de caracteres convertidas a enteros.  El ejemplo siguiente genera C2015:  
  
```  
// C2015b.cpp  
#include <stdio.h>  
  
int main()   
{  
    int a = 'abcde';   // C2015  
  
    int b = 'a';   // 'a' = ascii 0x61  
    printf_s("%x\n", b);  
}  
```