---
title: C. Gramática de OpenMP C y C++
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 85e18161079b49e83cc9fedb3184ee220c889e75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362951"
---
# <a name="c-openmp-c-and-c-grammar"></a>C. Gramática de OpenMP C y C++

[C.1 Notación](#c1-notation)<br/>
[C.2 Reglas](#c2-rules)

## <a name="c1-notation"></a>C.1 Notación

Las reglas de gramática constan del nombre de un no terminal, seguido de dos puntos, seguido de alternativas de reemplazo en líneas independientes.

El término de la expresión sintáctica<sub>opt</sub> indica que el término es opcional en el reemplazo.

La expresión sintáctica *término*<sub>optseq</sub> es equivalente a *término-seq*<sub>opt</sub> con las siguientes reglas adicionales:

*term-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Término*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq* *term*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq*   `,` *term*

## <a name="c2-rules"></a>C.2 Reglas

La notación se describe en la sección 6.1 del estándar C. Este apéndice gramática muestra las extensiones para la gramática del lenguaje de base para las directivas de OpenMP C y C++.

**/\* in C++ (ISO/IEC 14882:1998) \*/**

*statement-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-seq statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-seq openmp-directive*

**/\* en C90 ISO/IEC 9899 (puede: en 1990) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de la lista de instrucciones*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista de instrucciones de directiva de openmp*

**/\* en C99 (ISO/IEC 9899: 1999) \*/**

*block-item*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*

**/\* instrucciones estándar \*/**

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-construct*

*openmp-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*para la construcción*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción de secciones*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción de único*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción Critical*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Atomic (construcción):*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción ordenada*

*openmp-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrier-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*flush-directive*

*structured-block*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*

*parallel-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de paralelo directiva*

*parallel-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel` *parallel-clause*<sub>optseq</sub> *new-line*

*parallel-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*unique-parallel-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (` *Expresión*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (` *Expresión*   `)`

*for-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de iteración de directiva*

*for-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for` *for-clause*<sub>optseq</sub> *new-line*

*for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*unique-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *schedule-kind*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *tipo de programación* `,` *expresión*   `)`

*schedule-kind*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ámbito de la sección Directiva de secciones*

*sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections` *sections-clause*<sub>optseq</sub> *new-line*

*sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*ámbito de la sección*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{sección secuencia}*

*section-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-directive*<sub>opt</sub> *structured-block*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*secuencia en la sección Directiva de sección estructurado bloques*

*section-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section` *new-line*

*single-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de única directiva*

*single-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single` *single-clause*<sub>optseq</sub> *new-line*

*single-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*parallel-for-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de iteración paralela de directiva*

*parallel-for-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for` *parallel-for-clause*<sub>optseq</sub> *new-line*

*parallel-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*parallel-sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ámbito de la sección Directiva paralelo-secciones*

*parallel-sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections` *parallel-sections-clause*<sub>optseq</sub> *new-line*

*parallel-sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*master-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de master-(directiva)*

*master-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master` *new-line*

*critical-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de directiva Critical*

*critical-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical` *region-phrase*<sub>opt</sub> *new-line*

*region-phrase*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identificador)*

*barrier-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier` *new-line*

*atomic-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de expresión de directiva atomic*

*atomic-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic` *new-line*

*flush-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush` *flush-vars*<sub>opt</sub> *new-line*

*flush-vars*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(variable-list)*

*ordered-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de directiva ordenada*

*ordered-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered` *new-line*

**/\* declaraciones estándares \*/**

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva threadprivate*

*threadprivate-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (` *variable-list*    `)` *new-line*

*data-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (` *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *reduction-operator*    `:`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *variable-list*    `)`

*reduction-operator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Uno de:   `+ \* - & ^ | && ||`

**/\* en C \*/**

*variable-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *identifier*

**/\* en C++ \*/**

*variable-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Id. de expresión*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *id-expression*
