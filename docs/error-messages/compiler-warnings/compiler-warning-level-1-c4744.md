---
title: "Advertencia del compilador (nivel 1) C4744 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4744"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4744"
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4744
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' tiene un tipo diferente en 'archivo1' y 'archivo2': 'tipo1' y 'tipo2'  
  
 Una variable externa definida o a la que se hizo referencia en dos archivos tiene diferente alineación en dichos archivos.  Para resolverlo, haga las definiciones de tipo iguales o cambie el nombre de la variable en uno de los archivos.  
  
 Solo se emite C4744 cuando los archivos se compilan con \/GL.  Para obtener más información, vea [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md).  
  
> [!NOTE]
>  C4744 aparece normalmente en archivos C \(no C\+\+\), porque en C\+\+ un nombre de variable se decora con información de tipo.  Cuando el ejemplo \(abajo\) se compila como C\+\+, obtendrá el error del vinculador LNK2019.  
  
## Ejemplo  
 Este ejemplo contiene la primera definición.  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4744.  
  
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