---
title: True (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb810f880ac86651059d71a59040e34810c7e167
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464777"
---
# <a name="true-c"></a>true (C++)
## <a name="syntax"></a>Sintaxis  
  
```  
bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta palabra clave es uno de los dos valores de una variable de tipo [bool](../cpp/bool-cpp.md) o una expresión condicional (una expresión condicional es ahora una expresión booleana true). Si `i` es de tipo **bool**, a continuación, la instrucción `i = true;` asigna **true** a `i`.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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