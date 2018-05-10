---
title: C.2 reglas | Documentos de Microsoft
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
ms.openlocfilehash: a3bdf26435fdfeea2196b9ef281d656805f51bf2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="c2-rules"></a>C.2 Reglas
La notación se describe en la sección 6.1 del estándar C. Este apéndice gramática muestra las extensiones de la gramática del lenguaje de base para las directivas de OpenMP C y C++.  
  
 **/\* en C++ (ISO/IEC 14882: 1998) \*/**  
  
 *instrucción-seq*:  
  
 *statement*  
  
 *Directiva de OpenMP*  
  
 *instrucción de declaración-seq*  
  
 *instrucción-seq directiva de openmp*  
  
 **/\* en C90 ISO/IEC 9899 (puede: en 1990) \*/**  
  
 *statement-list*:  
  
 *statement*  
  
 *Directiva de OpenMP*  
  
 *statement-list statement*  
  
 *lista de instrucciones de directiva de openmp*  
  
 **/\* en C99 (ISO/IEC 9899: 1999) \*/**  
  
 *elemento de bloque*:  
  
 *declaration*  
  
 *statement*  
  
 *Directiva de OpenMP*  
  
 *statement*:  
  
 **/\* instrucciones estándar \*/**  
  
 *construcción de OpenMP*  
  
 *construcción de OpenMP*:  
  
 *construcción paralela*  
  
 *para construir*  
  
 *construcción de secciones*  
  
 *construcción único*  
  
 *paralelo de construcción*  
  
 *construcción de secciones paralelo*  
  
 *Master construc*  
  
 *Critical (construcción):*  
  
 *Atomic (construcción):*  
  
 *construcción ordenada*  
  
 *Directiva de OpenMP*:  
  
 *Directiva de barrera*  
  
 *Directiva de vaciado*  
  
 *bloque estructurado*:  
  
 *statement*  
  
 *construcción paralelo*:  
  
 *bloque estructurado de directiva paralelo*  
  
 *Directiva paralelo*:  
  
 **# pragma omp parallel***cláusula paralelo*optseq *nueva línea*   
  
 *cláusula paralelo*:  
  
 *cláusula UNIQUE paralelo*  
  
 *cláusula de datos*  
  
 *cláusula UNIQUE paralelo*:  
  
 **Si (** *expresión* **)**  
  
 **num_threads (** *expresión* **)**  
  
 *para la construcción de*:  
  
 *instrucción de iteración de directiva*  
  
 *para la directiva de*:  
  
 **# pragma omp para** *cláusula for*optseq *nueva línea*  
  
 *cláusula for*:  
  
 *único para la cláusula*  
  
 *cláusula de datos*  
  
 **nowait**  
  
 *único para la cláusula*:  
  
 **ordenada**  
  
 **programación (** *tipo de programación* **)**  
  
 **programación (** *tipo de programación* **,** *expresión* **)**  
  
 *tipo de programación*:  
  
 **static**  
  
 **dynamic**  
  
 **guiadas por perfiles**  
  
 **En tiempo de ejecución**  
  
 *construcción de secciones*:  
  
 *ámbito de sección Directiva de secciones*  
  
 *Directiva de secciones*:  
  
 **secciones de # pragma omp** *cláusula secciones*optseq *nueva línea*  
  
 *cláusula de secciones*:  
  
 *cláusula de datos*  
  
 **nowait**  
  
 *ámbito de la sección*:  
  
 *{sección secuencia}*  
  
 *secuencia de la sección*:  
  
 *Directiva de sección*opt *bloque estructurado*  
  
 *secuencia de la sección Directiva de sección estructurado bloque*  
  
 *Directiva de sección*:  
  
 **# pragma omp section** *nueva línea*  
  
 *construcción único*:  
  
 *bloque estructurado de directiva único*  
  
 *Single-directive*:  
  
 **# pragma omp único** *única cláusula*optseq *nueva línea*  
  
 *cláusula único*:  
  
 *cláusula de datos*  
  
 **nowait**  
  
 *paralelo para construir*:  
  
 *instrucción de iteración de paralelo de directiva*  
  
 *paralelo para directiva*:  
  
 **# pragma omp parallel para** *cláusula for paralelo*optseq *nueva línea*  
  
 *cláusula for paralelo*:  
  
 *cláusula UNIQUE paralelo*  
  
 *único para la cláusula*  
  
 *cláusula de datos*  
  
 *construcción de secciones paralelo*:  
  
 *ámbito de sección Directiva de sections paralelo*  
  
 *Directiva de sections paralelo*:  
  
 **secciones de # pragma omp parallel** *paralelo-secciones-clause*optseq *nueva línea*  
  
 *cláusula de secciones paralelo*:  
  
 *cláusula UNIQUE paralelo*  
  
 *cláusula de datos*  
  
 *construcción de master*:  
  
 *bloque estructurado de directiva de master*  
  
 *Directiva de master*:  
  
 **patrón de # pragma omp** *nueva línea*  
  
 *Critical (construcción)-*:  
  
 *bloque estructurado de directiva Critical*  
  
 *Directiva Critical*:  
  
 **# pragma omp crítico** *región frase*opt *nueva línea*  
  
 *frase de región*:  
  
 *(identificador)*  
  
 *Directiva de barrera*:  
  
 **barrera de # pragma omp** *nueva línea*  
  
 *Atomic (construcción)-*:  
  
 *instrucción de expresión de directiva atómica*  
  
 *directiva atomic*:  
  
 **# pragma omp atomic** *nueva línea*  
  
 *Directiva de vaciado*:  
  
 **# pragma omp vaciado** *vaciado var*opt *nueva línea*  
  
 *variables de los de vaciado*:  
  
 *(lista de variables)*  
  
 *construcción ordenada*:  
  
 *bloque estructurado de directiva ordenada*  
  
 *Directiva ordenados*:  
  
 **# pragma omp ordenados** *nueva línea*  
  
 *Declaración*:  
  
 **/\* declaraciones estándares \*/**  
  
 *Directiva threadprivate*  
  
 *Directiva threadprivate*:  
  
 **# pragma omp threadprivate (** *lista de variables***)** *nueva línea*   
  
 *cláusula de datos*:  
  
 **privada (** *lista de variables* **)**  
  
 **copyprivate (***lista de variables***)**   
  
 **firstprivate (***lista de variables***)**   
  
 **lastprivate (** *lista de variables***)**   
  
 **compartido (** *lista de variables* **)**  
  
 **predeterminado (compartido)**  
  
 **predeterminado (ninguno)**  
  
 **reducción (***operador de reducción***:***lista de variables***)**   
  
 **copyin (***lista de variables***)**   
  
 *operador de reducción*:  
  
 *Uno de*:  **+  \* -& ^ &#124; & &&#124;&#124;**  
  
 **/\* en C \*/**  
  
 *lista de variables*:  
  
 *identifier*  
  
 *lista de variables* **,** *identificador*  
  
 **/\* en C++ \*/**  
  
 *lista de variables*:  
  
 *Id. de expresión*  
  
 *lista de variables* **,** *expresión de Id.*