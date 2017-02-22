---
title: "Advertencia del compilador (nivel 4) C4256 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4256"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4256"
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 4) C4256
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : el constructor para la clase con bases virtuales tiene '...'; puede que las llamadas no sean compatibles con versiones anteriores de Visual C\+\+  
  
 Posible incompatibilidad.  
  
 Considere el ejemplo de código siguiente.  Si la definición del constructor S2::S2 \(int i,… \) se compiló con una versión del compilador de Visual C\+\+ antes de la versión 7. pero el ejemplo siguiente se compila con la versión actual, la llamada al constructor para S3 no funcionaría correctamente debido a un cambio de convención de llamada de especial\- caso.  Si ambos observarse mediante Visual C\+\+ 6,0, la llamada no funcionaría muy la derecha ninguno, a menos que no se pasen parámetros en los puntos suspensivos.  
  
 Para resolver este advertencia:  
  
1.  No utilice puntos suspensivos en un constructor.  
  
2.  Asegúrese de que todos los componentes del proyecto se compilan con la versión actual \(incluida cualquier biblioteca que pueda definir o hacer referencia a esta clase\) y, a continuación, deshabilite la advertencia con la directiva pragma [warning](../../preprocessor/warning.md).  
  
 El código siguiente genera el error C4256:  
  
```  
// C4256.cpp  
// compile with: /W4  
// #pragma warning(disable : 4256)  
struct S1  
{  
};  
  
struct S2: virtual public S1  
{  
   S2( int i, ... )    // C4256  
   {  
      i = 0;  
   }  
   /*  
   // try the following line instead  
   S2( int i)  
   {  
      i = 0;  
   }  
   */  
};  
  
void func1()  
{  
   S2 S3( 2, 1, 2 );   // C4256  
   // try the following line instead  
   // S2 S3( 2 );  
}  
  
int main()  
{  
}  
```