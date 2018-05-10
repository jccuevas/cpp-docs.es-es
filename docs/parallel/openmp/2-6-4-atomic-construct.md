---
title: 2.6.4 atomic (construcción) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66f0dc8469d1d70b2697df1fe120f10142d90dbe
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="264-atomic-construct"></a>2.6.4 atomic (Construcción)
El `atomic` Directiva garantiza que una ubicación de memoria específica se actualiza de forma atómica, en lugar de exponer a la posibilidad de que varios subprocesos de escritura simultáneas. La sintaxis de la `atomic` directiva es como sigue:  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 La instrucción de expresión debe tener una de las siguientes formas:  
  
 *x binop*= *expr*  
  
 x ++.  
  
 ++ x  
  
 x:  
  
 --x  
  
 En las expresiones anteriores:  
  
-   *x* es una expresión de valor l con tipo escalar.  
  
-   *Expr* es una expresión con un tipo escalar y no hace referencia el objeto designado por *x*.  
  
-   `binop` no es un operador sobrecargado y es uno de +, *, -, / &, ^, &#124;, <\<, o >>.  
  
 Aunque es definido por la implementación si una implementación reemplaza todas `atomic` directivas con **crítico** directivas que tengan el mismo único *nombre*, el `atomic` (directiva) permite una mejor optimización. A menudo las instrucciones de hardware están disponibles que puede realizar la actualización atómica con la menor carga.  
  
 Solo los carga y la memoria del objeto designado por *x* son atómico; la evaluación de *expr* no es atómica. Para evitar condiciones de carrera, todas las actualizaciones de la ubicación en paralelo deben protegerse con la `atomic` directiva, excepto las que se sabe que están libres de las condiciones de carrera.  
  
 Restricciones a la `atomic` directiva son los siguientes:  
  
-   Todas las referencias atómicas a la ubicación de almacenamiento x a lo largo del programa deben tener un tipo compatible.  
  
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