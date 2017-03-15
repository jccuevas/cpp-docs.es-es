---
title: "A.20   Binding of barrier Directives | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.20   Binding of barrier Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La llamada directiva de las reglas de enlace para que una directiva de **barrera** enlace a `parallel` la directiva que agrega más próxima.  Para obtener más información sobre el enlace de directivas, vea [sección 2,8](../../parallel/openmp/2-8-directive-binding.md) en la página 32.  
  
 En el ejemplo siguiente, la llamada *de main* *en sub2* es bajo porque **barrera** \(en *sub3*\) enlazado a la región paralela en *sub2*.  La llamada *de main* *en sub1* es bajo porque **barrera** enlazado a la región paralela en la subrutina *sub2*.  La llamada *de main* *a sub3* es bajo porque **barrera** no enlaza a ninguna región paralela y se omite.  Observe también que **barrera** sólo sincroniza el equipo de subprocesos de la región paralela que agrega y no todos los subprocesos creados en *sub1*.  
  
```  
int main()  
{  
    sub1(2);  
    sub2(2);  
    sub3(2);  
}  
  
void sub1(int n)  
{  
    int i;  
    #pragma omp parallel private(i) shared(n)  
    {  
        #pragma omp for  
        for (i=0; i<n; i++)  
            sub2(i);  
    }  
}  
  
void sub2(int k)  
{  
     #pragma omp parallel shared(k)  
     sub3(k);  
}  
  
void sub3(int n)  
{  
    work(n);  
    #pragma omp barrier  
    work(n);  
}  
```