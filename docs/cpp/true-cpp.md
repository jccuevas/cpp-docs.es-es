---
title: True (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: true_cpp
dev_langs: C++
helpviewer_keywords: true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 453857447c9bf0b07cd40d9158d7e2ed0ba0121f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="true-c"></a>true (C++)
## <a name="syntax"></a>Sintaxis  
  
```  
  
      bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta palabra clave es uno de los dos valores de una variable de tipo [bool](../cpp/bool-cpp.md) o una expresión condicional (una expresión condicional es ahora una expresión booleana true). Si `i` es de tipo `bool`, a continuación, la instrucción `i = true;` asigna **true** a `i`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// bool_true.cpp  
#include <stdio.h>  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
```Output  
1  
0  
```  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)