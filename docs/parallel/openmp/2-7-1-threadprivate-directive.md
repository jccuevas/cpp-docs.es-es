---
title: "2.7.1 threadprivate Directive | Microsoft Docs"
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
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.1 threadprivate Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de `threadprivate` crea el archivo\-ámbito denominado, el espacio de nombres\-ámbito, o las variables estáticas de bloque\-ámbito especificadas en private *de la variable\-lista* a un subproceso.  *la variable\-lista* es una lista separada por comas de variables que no tienen un tipo incompleto.  La sintaxis de la directiva de `threadprivate` es la siguiente:  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 Cada copia de una variable de `threadprivate` inicializa una vez, en un punto sin especificar en el programa antes de la primera referencia a esa copia, y en la forma habitual \(es decir, como la copia maestra se inicializa en una ejecución en serie del programa\).  Observe que si un objeto se hace referencia en un inicializador explícito de una variable de `threadprivate` , y el valor del objeto se modifica antes de la primera referencia a una copia de la variable, el comportamiento no está especificado.  
  
 Como con ninguna variable privada, un subproceso no debe hacer referencia a la copia de otro subproceso de un objeto de `threadprivate` .  Durante las regiones en serie y áreas principales del programa, las referencias estarán a la copia del subproceso principal del objeto.  
  
 Después de la primera región paralela se ejecute, los datos de los objetos de `threadprivate` se garantiza para conservar sólo si se ha deshabilitado el mecanismo dinámico de subprocesos y si permanece el número de subprocesos sin cambiar para todas las regiones paralelas.  
  
 Restricciones de la directiva de `threadprivate` son los siguientes:  
  
-   Una directiva de `threadprivate` para variables de archivo\-ámbito o espacio de nombres\-ámbito debe aparecer fuera de cualquier definición o declaración, y debe preceder léxico todas las referencias a variables cualquiera de los en la lista.  
  
-   Cada variable de *la variable\-lista* de una directiva de `threadprivate` en el ámbito de archivo o de espacio de nombres debe hacer referencia a una declaración de variable en el ámbito del archivo o el espacio de nombres que precede léxicamente a la directiva.  
  
-   Una directiva de `threadprivate` para las variables estáticas de bloque\-ámbito debe aparecer en el ámbito de la variable y no en un ámbito anidado.  La directiva debe preceder léxico todas las referencias a variables cualquiera de los en la lista.  
  
-   Cada variable de *la variable\-lista* de una directiva de `threadprivate` en ámbito de bloque debe hacer referencia a una declaración de variable en el mismo ámbito que precede léxicamente a la directiva.  La declaración de variable debe usar el especificador static de la clase de almacenamiento.  
  
-   Si una variable se especifica en una directiva de `threadprivate` en una unidad de traducción, debe especificarse en una directiva de `threadprivate` en cada unidad de traducción en la que se declara.  
  
-   una variable de `threadprivate` no debe aparecer en ninguna cláusula excepto `copyin`, `copyprivate`, `schedule`, `num_threads`, o la cláusula de **If \[SQL2008\]** .  
  
-   la dirección de una variable de `threadprivate` no es una constante de dirección.  
  
-   una variable de `threadprivate` no debe tener un tipo incompleto o un tipo de referencia.  
  
-   Una variable de `threadprivate` con el tipo de clase POD debe tener un constructor accesible, inequívoca de copia si se declara con un inicializador explícito.  
  
 El ejemplo siguiente se muestra cómo la modificación de una variable que aparece en un inicializador puede producir un comportamiento no especificado, y también cómo evitar este problema mediante un objeto auxiliar y un constructor.  
  
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
  
## referencias cruzadas:  
  
-   Los subprocesos dinámicos, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39.  
  
-   la variable de entorno`OMP_DYNAMIC` , vea [sección 4,3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.