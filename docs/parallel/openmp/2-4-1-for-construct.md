---
title: "2.4.1 for Construct | Microsoft Docs"
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
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4.1 for Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de **Para** identifica una construcción iterativa de división del trabajo que especifica que las iteraciones del bucle asociado se ejecutan en paralelo.  Las iteraciones del bucle de **Para** se enrutan a través de los subprocesos que ya existen en el equipo que ejecuta la construcción paralela a la que enlaza.  La sintaxis de construcción de **Para** es la siguiente:  
  
```  
#pragma omp for [clause[[,] clause] ... ] new-line  
   for-loop  
```  
  
 La cláusula es:  
  
 *variable\-lista* **\)**de**private \(**  
  
 *variable\-lista* **\)**de**firstprivate \(**  
  
 *variable\-lista* **\)**de**lastprivate \(**  
  
 *variable\-lista* **\)**de**:**de*operador de***detallado \(**  
  
 **consultar**  
  
 *clase de* **programación \(**\[, *chunk\_size*\]**\)**  
  
 **nowait**  
  
 La directiva de **Para** coloca las restricciones en la estructura de bucle correspondiente de **Para** .  específicamente, el bucle correspondiente de **Para** debe tener forma canónica:  
  
 *b lógico\-de Op. Sys. de* **para \(** init\-*expr***;***var*; *aumento\-expr***\)**  
  
 *init\-expr*  
 Uno de los siguientes:  
  
 *var* \= *libra*  
  
 *entero\-tipo var* \= *libra*  
  
 *aumento\-expr*  
 Uno de los siguientes:  
  
 \+\+var  
  
 *var* \+\+  
  
 \-\- *var*  
  
 *var* \-\-  
  
 *aumento* *var* \+\=  
  
 *var* \- \= *aumenta*  
  
 *var* \= *var* \+ *aumentado*  
  
 *var* \= *aumentado* \+ *var*  
  
 *var* \= *var* \- *incr*  
  
 *var*  
 Una variable de entero con signo.  Si esta variable sería compartida de otra forma, implícita se crea privada para la duración del párrafo.  Esta variable no se debe modificar en el cuerpo de la instrucción de **Para** .  A menos que sea **lastprivate**especificado, su valor después del bucle es indeterminado.  
  
 *lógico\-de Op. Sys.*  
 Uno de los siguientes:  
  
 \<  
  
 \<\=  
  
 \>  
  
 \>\=  
  
 *signo de número*, *b*, y *ampliación*  
 Expresiones de entero invariables de bucle.  No hay ninguna sincronización durante la evaluación de estas expresiones.  Así, los efectos secundarios evaluado genera resultados indeterminados.  
  
 Observe que la forma canónica permite que el número de iteraciones del bucle se calcula en la entrada al bucle.  Este cálculo se realiza con valores en el tipo *de var*, después de promociones enteras.  En concreto, si valor *b* \- *la libra* \+ *aumentado* no se puede representar en ese tipo, el resultado es indeterminado.  Además, si *es lógico\-de Op. Sys.* es \< o \<\= a *aumento\-expr* debe producir *var* el aumento en cada iteración del bucle.  Si *es lógico\-de Op. Sys.* es \> o \>\= a *aumento\-expr* debe producir *var* disminuya en cada iteración del bucle.  
  
 La cláusula de **programación** especifica cómo las iteraciones del bucle de **Para** se dividen entre los subprocesos del equipo.  La corrección de un programa no debe depender del subproceso ejecuta una iteración determinada.  El valor de *chunk\_size*, si se especifica, debe ser una expresión de tipo entero invariable de bucle con un valor positivo.  No hay ninguna sincronización durante la evaluación de esta expresión.  Así, los efectos secundarios evaluado genera resultados indeterminados.  *La clase* de programación puede ser una de las siguientes:  
  
 Los valores *de la clase* de cláusula de **programación** FRAME 2\-1  
  
|||  
|-|-|  
|static|Cuando **programación \(static,** *chunk\_size*se especifica**\)** , las iteraciones se divide en partes de un tamaño especificado por *chunk\_size*.  Los elementos se asignan estáticamente a los subprocesos en el equipo de forma circular en el orden del número de subprocesos.  Cuando no *chunk\_size* se especifica, el espacio de la iteración se divide en partes que ocupan aproximadamente iguales de tamaño, con un fragmento asignado a cada subproceso.|  
|dynamic|Cuando **programe \(dinámico,** *chunk\_size*se especifica**\)** , las iteraciones se divide en una serie de fragmentos, el cada contener *chunk\_size* iteraciones.  Cada fragmento se asigna a un subproceso que está esperando una asignación.  El subproceso ejecuta el fragmento de iteraciones y después espera la siguiente asignación, hasta que ningún partes queden asignar.  Observe que la pieza último asignarlos puede tener un número menor de iteraciones.  Cuando no *chunk\_size* se especifica, se toma como valor predeterminado la 1.|  
|dirigido|Cuando **programación \(ejecuta,** *chunk\_size*se especifica**\)** , las iteraciones se asigna a los subprocesos en fragmentos a reducir los tamaños.  Cuando un subproceso finaliza su parte asignado de iteraciones, se asigna dinámicamente otro fragmento, hasta que queda ninguna.  Para *un chunk\_size* de 1, el tamaño de cada fragmento es aproximadamente el número de iteraciones no asignadas dividen por el número de subprocesos.  Estos tamaños disminuyen aproximadamente exponencial en 1.  Para *un chunk\_size* con *k* de valor mayor que 1, los tamaños disminuye aproximadamente exponencial *a k*, salvo que la pieza último puede tener menos que iteraciones *de k* .  Cuando no *chunk\_size* se especifica, se toma como valor predeterminado la 1.|  
|motor en tiempo de ejecución|Cuando se especifica **programación \(en tiempo de ejecución\)** , la decisión referente a la programación se aplaza hasta el tiempo de ejecución.  *La clase* de programación y el tamaño de los sectores se pueden elegir en tiempo de ejecución estableciendo la variable de entorno **OMP\_SCHEDULE**.  Si esta variable de entorno no está establecida, la programación resultante es implementación\-definido.  Cuando se especifica **programación \(en tiempo de ejecución\)** , *chunk\_size* no debe especificar.|  
  
 En ausencia de una cláusula definidas explícitamente de **programación** , **programación** predeterminado es implementación\-definido.  
  
 Un programa de OpenMP\-conforme a no debe confiar en una programación determinada para la ejecución correcta.  Un programa no debe depender de *una clase* de programación que cumple exacto a la descripción especificada anteriormente, porque es posible tener variaciones en las implementaciones de la misma *clase* de programación entre diferentes compiladores.  Las descripciones se pueden utilizar para seleccionar la programación adecuada para un escenario determinado.  
  
 La cláusula de **consultar** debe estar presente en que las directivas de **consultar** enlazados a **Para** la construcción.  
  
 Hay una barrera implícita al final de una construcción de **Para** a menos que se especifique una cláusula de **nowait** .  
  
 Restricciones de la directiva de **Para** son los siguientes:  
  
-   El bucle de **Para** debe ser un bloque estructurado, y, además, la ejecución no se debe terminar con una instrucción de **Inter** .  
  
-   Los valores de las expresiones de control de bucle de bucle de **Para** asociado con una directiva de **Para** deben ser el mismo para todos los subprocesos en el equipo.  
  
-   La variable de iteración del bucle de **Para** debe tener un tipo con signo entero.  
  
-   Una sola cláusula de **programación** puede aparecer en una directiva de **Para** .  
  
-   Una sola cláusula de **consultar** puede aparecer en una directiva de **Para** .  
  
-   Una sola cláusula de **nowait** puede aparecer en una directiva de **Para** .  
  
-   No se especifica si o con qué frecuencia los efectos secundarios dentro *de chunk\_size*, *la libra*, el *b*, o de las expresiones *raise* aparece.  
  
-   El valor de la expresión *de chunk\_size* debe ser el mismo para todos los subprocesos en el equipo.  
  
## referencias cruzadas:  
  
-   **private**, **firstprivate**, **lastprivate**, y las cláusulas de **informe detallado** , vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.  
  
-   La variable de entorno**OMP\_SCHEDULE** , vea [sección 4,1](../../parallel/openmp/4-1-omp-schedule.md) en la página 48.  
  
-   la construcción de**consultar** , vea [sección 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) en la página 22.  
  
-   [apéndice d](../../parallel/openmp/d-using-the-schedule-clause.md), página 93, le ofrece más información sobre cómo utilizar la cláusula de programación.