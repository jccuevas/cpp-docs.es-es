---
title: C.2 reglas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb83b35a03608e272e9af67159b61e5dbf4e1ec6
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755026"
---
# <a name="c2-rules"></a>C.2 Reglas
La notación se describe en la sección 6.1 del estándar C. Este apéndice gramática muestra las extensiones para la gramática del lenguaje de base para las directivas de OpenMP C y C++.

**/\* en C++ (ISO/IEC 14882: 1998) \*/**

*instrucción seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva de OpenMP*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de declaración seq*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seq de instrucción de OpenMP*

**/\* en C90 ISO/IEC 9899 (puede: en 1990) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva de OpenMP*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de la lista de instrucciones*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista de instrucciones de directiva de openmp*

**/\* en C99 (ISO/IEC 9899: 1999) \*/**

*elemento de bloque*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Declaración*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva de OpenMP*

**/\* instrucciones estándar \*/**

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción de OpenMP*

*construcción de OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción de paralelo*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*para la construcción*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción de secciones*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción de único*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*paralelo de construcción*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción de secciones paralelo*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*patrón de construcción*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción Critical*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Atomic (construcción):*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*construcción ordenada*

*Directiva de OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva de barrera*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva de vaciado*

*bloque estructurado*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción*

*construcción de paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de paralelo directiva*

*Directiva de paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp parallel** *paralelo cláusula*<sub>optseq</sub> *nueva línea*

*cláusula de paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula UNIQUE paralelo*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula de datos*

*cláusula UNIQUE paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Si (** *expresión* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**num_threads (** *expresión* **)**

*para construir*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de iteración de directiva*

*para la directiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp para** *cláusula for*<sub>optseq</sub> *nueva línea*

*cláusula for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*único para la cláusula*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula de datos*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*único para la cláusula*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Ordenada**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**programación (** *tipo de programación* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**programación (** *tipo de programación* **,** *expresión* **)**

*tipo de programación*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Estático**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Dinámico**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**guiada por perfiles**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**En tiempo de ejecución**

*construcción de secciones*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ámbito de la sección Directiva de secciones*

*Directiva de secciones*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**secciones de # pragma omp** *secciones cláusula*<sub>optseq</sub> *nueva línea*

*cláusula de secciones*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula de datos*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*ámbito de la sección*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{sección secuencia}*

*secuencia en la sección*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva de sección*<sub>opt</sub> *bloque estructurado*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*secuencia en la sección Directiva de sección estructurado bloques*

*Directiva de sección*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp section** *nueva línea*

*construcción de solo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de única directiva*

*Directiva de solo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp único** *cláusula única*<sub>optseq</sub> *nueva línea*

*cláusula única*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula de datos*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*paralelo para construir*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de iteración paralela de directiva*

*paralelo para directiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp parallel para** *cláusula for paralelo*<sub>optseq</sub> *nueva línea*

*cláusula for paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula UNIQUE paralelo*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*único para la cláusula*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula de datos*

*construcción de secciones paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ámbito de la sección Directiva paralelo-secciones*

*Directiva de secciones paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**las secciones de # pragma omp parallel** *cláusula de secciones paralelo*<sub>optseq</sub> *nueva línea*

*cláusula de secciones paralelo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula UNIQUE paralelo*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cláusula de datos*

*patrón de construcción*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de master-(directiva)*

*Directiva de master*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**patrón de # pragma omp** *nueva línea*

*construcción Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de directiva Critical*

*Directiva Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp crítico** *región frase*<sub>opt</sub> *nueva línea*

*región frase*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identificador)*

*Directiva de barrera*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**barrera de # pragma omp** *nueva línea*

*Atomic (construcción)-*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de expresión de directiva atomic*

*directiva atomic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp atomic** *nueva línea*

*Directiva de vaciado*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp vaciado** *vaciado vars*<sub>opt</sub> *nueva línea*

*vaciado vars*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(lista de variables)*

*construcción ordenada*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bloque estructurado de directiva ordenada*

*Directiva ordenados*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pedido # pragma omp** *nueva línea*

**/\* declaraciones estándares \*/**

*declaración*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Directiva threadprivate*

*Directiva de threadprivate*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp threadprivate (** *lista de variables***)** *nueva línea* 

*cláusula de datos*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**privada (** *lista de variables* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyprivate (***lista de variables***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**firstprivate (***lista de variables***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**lastprivate (** *lista de variables***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**compartido (** *lista de variables* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**predeterminado (compartido)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**valor predeterminado (ninguna)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**reducción (***operador de reducción***:***lista de variables***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyin (***lista de variables***)** 

*operador de reducción*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Uno de:  **+  \* -& ^ &#124; & &&#124;&#124;**

**/\* en C \*/**

*lista de variables*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identificador*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista de variables* **,** *identificador*

**/\* en C++ \*/**

*lista de variables*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Id. de expresión*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista de variables* **,** *Id. de expresión*