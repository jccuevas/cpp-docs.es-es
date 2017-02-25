---
title: "Error del compilador C3020 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3020"
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : la variable de índice del bucle 'for' de OpenMP no se puede modificar en el cuerpo del bucle  
  
 Un bucle `for` de OpenMP no puede modificar el índice \(contador de bucle\) en el cuerpo del bucle `for`.  
  
 El código siguiente genera el error C3020:  
  
```  
// C3020.cpp  
// compile with: /openmp  
int main() {  
   int i = 0, n = 3;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; i < 10; i += n)  
         i *= 2;   // C3020  
         // try the following line instead  
         // n++;  
   }  
}  
```  
  
 Una variable declarada con [lastprivate](../../parallel/openmp/reference/lastprivate.md) no se puede utilizar como índice dentro de un bucle paralelizado.  
  
 El ejemplo siguiente generará el error C3020 para el segundo lastprivate porque desencadenará un escriba en idx\_a dentro del extremo del bucle.  La primera lastprivate no da error porque genera un escribir a idx\_a fuera del extremo del bucle \(técnicamente al final de la última iteración\)  El ejemplo siguiente genera el error C3020.  
  
```  
// C3020b.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_a)   // C3020  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```  
  
 En el ejemplo siguiente, se muestra una posible solución:  
  
```  
// C3020c.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_b)  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```