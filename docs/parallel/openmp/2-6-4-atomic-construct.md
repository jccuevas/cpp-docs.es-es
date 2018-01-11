---
title: "2.6.4 atomic (construcción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 629fff5b0bef507b775fbe1b5bfabadd50b790be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
-   `binop`no es un operador sobrecargado y es uno de +, *, -, / &, ^, &#124; <\<, o >>.  
  
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