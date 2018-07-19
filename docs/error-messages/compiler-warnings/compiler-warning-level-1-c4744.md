---
title: Compilador advertencia (nivel 1) C4744 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a45207f85575c8047f673b415ce802dbac24318
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282833"
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