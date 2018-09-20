---
title: 2.6.4 atomic (construcción) | Microsoft Docs
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
ms.openlocfilehash: f92e0b0c881ec1f8d54adce4a12f58ad514ed8f5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437487"
---
# <a name="264-atomic-construct"></a>2.6.4 atomic (Construcción)

El `atomic` Directiva garantiza que una ubicación de memoria específica se actualiza de forma atómica, en lugar de exponerlos a la posibilidad de múltiples simultáneas de escritura de subprocesos. La sintaxis de la `atomic` directiva es como sigue:

```
#pragma omp atomic new-lineexpression-stmt
```

La instrucción de expresión debe tener una de las siguientes formas:

*x binop*= *expr*

x ++

++ x

x--

--x

En las expresiones anteriores:

- *x* es una expresión de valor l con el tipo escalar.

- *Expr* es una expresión con tipo escalar, y no hace referencia el objeto designado por *x*.

- `binop` no es un operador sobrecargado y es uno de +, \*, -, / &, ^, &#124;, <\<, o >>.

Aunque es definido por la implementación si una implementación reemplaza toda `atomic` directivas con **críticos** directivas que tienen el mismo único *nombre*, el `atomic` directiva permite una mejor optimización. A menudo las instrucciones de hardware están disponibles que puede realizar la actualización atómica con la menor carga.

Solo la carga y el almacén del objeto designado por *x* son atómica; la evaluación de *expr* no es atómica. Para evitar condiciones de carrera, todas las actualizaciones de la ubicación en paralelo deben protegerse con el `atomic` la directiva, excepto los que se sabe que están libres de las condiciones de carrera.

Restricciones para el `atomic` directiva son los siguientes:

- Todas las referencias atómicas a la ubicación de almacenamiento x en todo el programa deben tener un tipo compatible.

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