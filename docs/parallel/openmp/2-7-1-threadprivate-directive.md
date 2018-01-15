---
title: 2.7.1 threadprivate (directiva) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22bb7f477be397f01ee4bd82f472ff26a26ce811
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate (Directiva)
El `threadprivate` directiva hace que el ámbito de archivo con nombre, ámbito de espacio de nombres o las variables de ámbito de bloque estáticas especificadas en el *lista de variables* privados de un subproceso. *lista de variables* es una lista separada por comas de variables que no tienen un tipo incompleto. La sintaxis de la `threadprivate` directiva es como sigue:  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 Cada copia de un `threadprivate` variable se inicializa una vez, en un punto especificado en el programa antes de la primera referencia a dicha copia y de la manera habitual (es decir, como la copia maestra se inicializaría en una ejecución en serie del programa). Tenga en cuenta que si se hace referencia a un objeto en un inicializador explícito de un `threadprivate` variable y el valor del objeto se modifica antes de la primera referencia a una copia de la variable, a continuación, el comportamiento no está especificado.  
  
 Como con cualquier variable privada, un subproceso no debe hacer referencia a copia de otro subproceso de un `threadprivate` objeto. Durante la serie y regiones maestra del programa, referencias será copia del subproceso principal del objeto.  
  
 Cuando se ejecuta la primera región paralela, los datos en el `threadprivate` se garantiza que los objetos para conservar solo si el mecanismo de subprocesos de dinámico se ha deshabilitado o si el número de subprocesos no se modifica para todas las regiones en paralelo.  
  
 Las restricciones a la `threadprivate` directiva son los siguientes:  
  
-   A `threadprivate` directiva para las variables de ámbito de archivo o en el ámbito de espacio de nombres debe aparecer fuera de cualquier definición o declaración y debe preceder léxicamente a todas las referencias a cualquiera de las variables en su lista.  
  
-   Cada variable en el *lista de variables* de un `threadprivate` directiva en el ámbito de archivo o espacio de nombres debe hacer referencia a una declaración de variable en el ámbito de archivo o espacio de nombres que precede léxicamente a la directiva.  
  
-   A `threadprivate` directiva para las variables de ámbito de bloque estáticos debe aparecer en el ámbito de la variable y no en un ámbito anidado. La directiva debe preceder léxicamente a todas las referencias a cualquiera de las variables en su lista.  
  
-   Cada variable en el *lista de variables* de un `threadprivate` (directiva) en el ámbito de bloque debe hacer referencia a una declaración de variable en el mismo ámbito que precede léxicamente a la directiva. La declaración de variable debe utilizar el especificador de clase de almacenamiento estática.  
  
-   Si se especifica una variable en un `threadprivate` directivas en una unidad de traducción, se debe especificar en una `threadprivate` la directiva en cada unidad de traducción en el que se declara.  
  
-   A `threadprivate` variable no debe aparecer en cualquier cláusula excepto la `copyin`, `copyprivate`, `schedule`, `num_threads`, o la **si** cláusula.  
  
-   La dirección de un `threadprivate` la variable no es una constante de dirección.  
  
-   Un `threadprivate` variable no debe tener un tipo incompleto o un tipo de referencia.  
  
-   Un `threadprivate` variable con tipo de clase POD no debe tener un constructor de copias sea accesible y no ambigua, si se declara con un inicializador explícito.  
  
 En el ejemplo siguiente se muestra cómo modificar una variable que aparece en un inicializador puede provocar un comportamiento no especificado así como a evitar este problema mediante el uso de un objeto auxiliar y un constructor de copias.  
  
```  
int x = 1;  
T a(x);  
const T b_aux(x); /* Capture value of x = 1 */  
T b(b_aux);  
#pragma omp threadprivate(a, b)  
  
void f(int n) {  
   x++;  
   #pragma omp parallel for  
   /* In each thread:  
   * Object a is constructed from x (with value 1 or 2?)  
   * Object b is copy-constructed from b_aux  
   */  
   for (int i=0; i<n; i++) {  
      g(a, b); /* Value of a is unspecified. */  
   }  
}  
```  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   Subprocesos dinámicos, consulte [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.  
  
-   `OMP_DYNAMIC`vea de variable de entorno [sección 4.3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.