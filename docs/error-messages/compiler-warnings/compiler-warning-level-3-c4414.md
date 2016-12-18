---
title: "Advertencia del compilador (nivel 3) C4414 | Microsoft Docs"
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
  - "C4414"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4414"
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4414
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : el salto short a la función se ha convertido a near  
  
 Los saltos short generan una instrucción compacta que se bifurca a una dirección dentro de un intervalo limitado desde la instrucción.  La instrucción incluye un desplazamiento SHORT que representa la distancia entre el salto y la dirección de destino, la definición de función.  Durante la vinculación, una función se puede mover o someter a optimizaciones en tiempo de vinculación que hagan que la función quede fuera del intervalo alcanzable desde un desplazamiento SHORT.  El compilador debe generar un registro especial para el salto, que requiere que la instrucción jmp sea NEAR o FAR.  El compilador realizó la conversión.  
  
 Por ejemplo, el código siguiente genera C4414:  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```