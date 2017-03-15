---
title: "C.2 Reglas | Microsoft Docs"
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
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C.2 Reglas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La notación se describe en la sección 6.1 del estándar C. Este apéndice gramática muestra las extensiones de la gramática del lenguaje base para las directivas de OpenMP C y C++.  
  
 **/\* en C++ (ISO/IEC 14882: 1998) \*/**  
  
 *instrucción-seq*:  
  
 *instrucción*  
  
 *Directiva de OpenMP*  
  
 *instrucción de declaración seq*  
  
 *seq de instrucción de directiva de openmp*  
  
 **/\* en C90 ISO/IEC 9899 (puede: en 1990) \*/**  
  
 *lista de instrucciones*:  
  
 *instrucción*  
  
 *Directiva de OpenMP*  
  
 *instrucción de la lista de instrucciones*  
  
 *lista de instrucciones de directiva de openmp*  
  
 **/\* en C99 (ISO/IEC 9899:1999) \*/**  
  
 *elemento de bloque*:  
  
 *declaración*  
  
 *instrucción*  
  
 *Directiva de OpenMP*  
  
 *instrucción*:  
  
 **/\* instrucciones estándar \*/**  
  
 *construcción de OpenMP*  
  
 *construcción de OpenMP*:  
  
 *construcción paralela*  
  
 *para la construcción*  
  
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
  
 *instrucción*  
  
 *construcción paralelo*:  
  
 *bloque estructurado de directiva paralelo*  
  
 *Directiva paralelo*:  
  
 **# pragma omp parallel**  *cláusula paralelo*optseq *nueva línea*  
  
 *cláusula paralelo*:  
  
 *cláusula UNIQUE paralelo*  
  
 *cláusula de datos*  
  
 *cláusula UNIQUE paralelo*:  
  
 **Si (** *expresión* **)**  
  
 **num_threads (** *expresión* **)**  
  
 *para la construcción de*:  
  
 *instrucción de iteración de directiva*  
  
 *para la directiva*:  
  
 **# pragma omp para** *cláusula for*optseq *nueva línea*  
  
 *cláusula for*:  
  
 *único para la cláusula*  
  
 *cláusula de datos*  
  
 **NOWAIT**  
  
 *único para la cláusula*:  
  
 **ordenada**  
  
 **programación (** *tipo de programación* **)**  
  
 **programación (** *tipo de programación* **,** *expresión* **)**  
  
 *tipo de programación*:  
  
 **estático**  
  
 **dinámico**  
  
 **guiada**  
  
 **en tiempo de ejecución**  
  
 *construcción de secciones*:  
  
 *ámbito de la sección Directiva secciones*  
  
 *Directiva de secciones*:  
  
 **secciones de omp pragma #** *cláusula secciones*optseq *nueva línea*  
  
 *cláusula de secciones*:  
  
 *cláusula de datos*  
  
 **NOWAIT**  
  
 *ámbito de la sección*:  
  
 *{sección secuencia}*  
  
 *secuencia en la sección*:  
  
 *Directiva de sección*opt *bloque estructurado*  
  
 *secuencia de la sección Directiva de sección estructurado bloque*  
  
 *Directiva de sección*:  
  
 **# pragma omp section** *nueva línea*  
  
 *construcción único*:  
  
 *bloque estructurado de directiva único*  
  
 *directiva solo*:  
  
 **# pragma omp único** *única cláusula*optseq *nueva línea*  
  
 *cláusula único*:  
  
 *cláusula de datos*  
  
 **NOWAIT**  
  
 *paralelo de construcción*:  
  
 *instrucción de iteración paralelo de directiva*  
  
 *paralelo de directiva*:  
  
 **# pragma omp parallel para** *cláusula for paralelo*optseq *nueva línea*  
  
 *cláusula for paralelo*:  
  
 *cláusula UNIQUE paralelo*  
  
 *único para la cláusula*  
  
 *cláusula de datos*  
  
 *construcción de secciones paralelo*:  
  
 *ámbito de sección Directiva de sections paralelo*  
  
 *Directiva de sections paralelo*:  
  
 **secciones paralelas de # pragma omp** *cláusula de secciones paralelo*optseq *nueva línea*  
  
 *cláusula de secciones paralelo*:  
  
 *cláusula UNIQUE paralelo*  
  
 *cláusula de datos*  
  
 *construcción del patrón*:  
  
 *Directiva maestra bloque estructurado*  
  
 *Directiva de master*:  
  
 **patrón de omp pragma #** *nueva línea*  
  
 *Critical (construcción)-*:  
  
 *bloque estructurado de directiva Critical*  
  
 *Directiva Critical*:  
  
 **# pragma omp crítica** *región frase*opt *nueva línea*  
  
 *frase de región*:  
  
 *(identificador)*  
  
 *Directiva de barrera*:  
  
 **barrera de omp pragma #** *nueva línea*  
  
 *Atomic (construcción)-*:  
  
 *instrucción de expresión de directiva atomic*  
  
 *directiva atomic*:  
  
 **# pragma omp atomic** *nueva línea*  
  
 *Directiva de vaciado*:  
  
 **# pragma omp vaciado** *vars vaciado*opt *nueva línea*  
  
 *vaciado vars*:  
  
 *(lista de variables)*  
  
 *construcción ordenada*:  
  
 *bloque estructurado de directiva ordenada*  
  
 *Directiva ordenados*:  
  
 **pedido # pragma omp** *nueva línea*  
  
 *declaración*:  
  
 **/\* declaraciones estándares \*/**  
  
 *Directiva threadprivate*  
  
 *Directiva threadprivate*:  
  
 **# pragma omp threadprivate (** *lista variable*  **)** *nueva línea*  
  
 *cláusula de datos*:  
  
 **privada (** *lista variable* **)**  
  
 **copyprivate (**  *lista variable*  **)**  
  
 **firstprivate (**  *lista variable*  **)**  
  
 **lastprivate (** *lista variable*  **)**  
  
 **compartido (** *lista variable* **)**  
  
 **valor predeterminado (compartido)**  
  
 **valor predeterminado (ninguna)**  
  
 **reducción (**  *operador de reducción*  **:**  *lista variable*  **)**  
  
 **copyin (**  *lista variable*  **)**  
  
 *operador de reducción*:  
  
 *Uno de*: **+ \* -& ^ & #124; & & & #124; & #124;**  
  
 **/\* en C \*/**  
  
 *lista de variables*:  
  
 *identificador*  
  
 *lista de variables* **,** *identificador*  
  
 **/\* en C++ \*/**  
  
 *lista de variables*:  
  
 *expresión de Id.*  
  
 *lista de variables* **,** *expresión de Id.*