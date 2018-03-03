---
title: Compilador advertencia (nivel 1) C4744 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b6fa95f8477f889aa8664d2b6d99c753cb9848d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4744"></a>Advertencia del compilador (nivel 1) C4744
'var' tiene un tipo diferente en 'archivo1' y 'archivo2': 'type1' y 'type2'  
  
 Una variable externa al que hace referencia o definida en dos archivos tiene distintos tipos en dichos archivos.  Para resolver, hacer que las definiciones de tipo el mismo, o cambiar el nombre de variable en uno de los archivos.  
  
 Se emite C4744 cuando los archivos se compilan con/GL.  Para obtener más información, consulte [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).  
  
> [!NOTE]
>  C4744 aparece normalmente en los archivos de C (no C++), porque en C++ un nombre de variable se decora con información de tipo.  Cuando el ejemplo (abajo) se compila como C++, obtendrá el error del vinculador LNK2019.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo contiene la primera definición.  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4744.  
  
```  
// C4744b.c  
// compile with: C4744.c /GL /W1  
// C4744 expected  
#include <stdio.h>  
  
extern unsigned global;  
  
main()   
{  
    printf_s("%d\n", global);  
}  
```