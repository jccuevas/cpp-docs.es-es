---
title: 2.7.1 threadprivate (Directiva)
ms.date: 11/04/2016
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
ms.openlocfilehash: 0ba5ea4892d70458f0f63bcb5b92968b36235273
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647010"
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate (Directiva)

El `threadprivate` directiva hace que el ámbito de archivo con nombre, ámbito de espacio de nombres o variables estáticas del ámbito de bloque especificadas en el *variable lista* privados de un subproceso. *lista de variables* es una lista separada por comas de variables que no tienen un tipo incompleto. La sintaxis de la `threadprivate` directiva es como sigue:

```
#pragma omp threadprivate(variable-list) new-line
```

Cada copia de un `threadprivate` variable se inicializa una vez, en un punto especificado en el programa antes de la primera referencia a esa copia y de la forma habitual (es decir, como la copia maestra se inicializaría en una ejecución en serie del programa). Tenga en cuenta que si se hace referencia a un objeto en un inicializador explícito de un `threadprivate` variable y el valor del objeto se modifica antes de la primera referencia a una copia de la variable y, después, el comportamiento no está especificado.

Como con cualquier variable privada, un subproceso no debe hacer referencia a copia de otro subproceso de un `threadprivate` objeto. Durante la serie y regiones principales del programa, las referencias será copia del subproceso principal del objeto.

Una vez que se ejecuta la primera región paralela, los datos en el `threadprivate` se garantiza que los objetos para conservar solo si los subprocesos del mecanismo dinámico se ha deshabilitado, y si el número de subprocesos permanece sin cambios para todas las regiones en paralelo.

Las restricciones para el `threadprivate` directiva son los siguientes:

- Un `threadprivate` debe aparecer fuera de cualquier definición o declaración de directiva para las variables de ámbito de archivo o el ámbito de espacio de nombres y debe preceder léxicamente a todas las referencias a cualquiera de las variables en su lista.

- Cada variable en el *lista de variables* de un `threadprivate` directiva en el ámbito de archivo o espacio de nombres debe hacer referencia a una declaración de variable en el ámbito de archivo o espacio de nombres que precede léxicamente a la directiva.

- Un `threadprivate` directiva para las variables de ámbito de bloque estática debe aparecer en el ámbito de la variable y no en un ámbito anidado. La directiva debe preceder léxicamente a todas las referencias a cualquiera de las variables en su lista.

- Cada variable en el *lista de variables* de un `threadprivate` directiva en el ámbito de bloque debe hacer referencia a una declaración de variable en el mismo ámbito que precede léxicamente a la directiva. La declaración de variable debe usar el especificador de clase de almacenamiento estática.

- Si se especifica una variable en un `threadprivate` la directiva en una unidad de traducción, se debe especificar en una `threadprivate` la directiva en cada unidad de traducción en el que se declara.

- Un `threadprivate` variable no debe aparecer en cualquier cláusula excepto el `copyin`, `copyprivate`, `schedule`, `num_threads`, o el **si** cláusula.

- La dirección de un `threadprivate` variable no es una constante de dirección.

- Un `threadprivate` variable no debe tener un tipo incompleto ni un tipo de referencia.

- Un `threadprivate` variable con tipo de clase POD no debe tener un constructor de copias sea accesible y no ambigua, si se declara con un inicializador explícito.

El ejemplo siguiente muestra cómo modificar una variable que aparece en un inicializador puede provocar un comportamiento no especificado y cómo evitar este problema mediante el uso de un objeto auxiliar y un constructor de copias.

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

- Subprocesos dinámicos, consulte [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.

- `OMP_DYNAMIC` vea variable de entorno [sección 4.3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.