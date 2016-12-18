---
title: "2.6.4 atomic (Construcci&#243;n) | Microsoft Docs"
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
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.4 atomic (Construcci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El `atomic` Directiva garantiza que una ubicación de memoria específica se actualiza de forma atómica, en lugar de exponer la posibilidad de múltiples simultáneas de subprocesos de escritura. La sintaxis de la `atomic` directiva es como sigue:  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 La instrucción de expresión debe tener una de las siguientes formas:  
  
 *x binop*= *expr*  
  
 x ++  
  
 ++ x  
  
 x:  
  
 x:  
  
 En las expresiones anteriores:  
  
-   *x* es una expresión de valor l a un tipo escalar.  
  
-   *Expr* es una expresión con tipo escalar y no hace referencia el objeto designado por *x*.  
  
-   `binop` no es un operador sobrecargado y es uno de +, *, -, / &, ^, &#124; <\<, o >>.  
  
 Aunque se define en la implementación si una implementación reemplaza todos `atomic` directivas con **crítica** directivas que tengan el mismo único *nombre*, el `atomic` directiva permite una mejor optimización. A menudo las instrucciones de hardware están disponibles que puede realizar la actualización atómica con la menor carga.  
  
 Sólo la carga y el almacén del objeto designado por *x* son atómica; la evaluación de *expr* no lo es. Para evitar condiciones de carrera, se deben proteger todas las actualizaciones de la ubicación en paralelo con la `atomic` Directiva, excepto los que se sabe que están libres de las condiciones de carrera.  
  
 Restricciones para el `atomic` Directiva son los siguientes:  
  
-   Todas las referencias atómicas a la ubicación de almacenamiento x en todo el programa deben tener un tipo compatible.  
  
## <a name="examples"></a>Ejemplos:  
  
```  
extern float a[], *p = a, b;  
/* Protect against races among multiple updates. */  
#pragma omp atomic  
a[index[i]] += b;  
/* Protect against races with updates through a. */  
#pragma omp atomic  
p[i] -= 1.0f;  
  
extern union {int n; float x;} u;  
/* ERROR - References through incompatible types. */  
#pragma omp atomic  
u.n++;  
#pragma omp atomic  
u.x -= 1.0f;  
```