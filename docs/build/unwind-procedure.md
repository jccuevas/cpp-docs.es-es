---
title: "Procedimiento para desenredar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Procedimiento para desenredar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La matriz de códigos de desenredo se organiza en orden descendente.  Cuando se produce una excepción, el sistema operativo almacena el contexto completo en un registro de contexto.  A continuación, se invoca la lógica de envío de excepciones, que ejecuta repetidamente los pasos siguientes para buscar un controlador de excepciones.  
  
1.  Use el valor de RIP actual almacenado en el registro de contexto para buscar una entrada de tabla de RUNTIME\_FUNCTION que describa la función actual \(o la parte de la función, en caso de entradas UNWIND\_INFO encadenadas\).  
  
2.  Si no se encuentra ninguna entrada de tabla de la función, entonces está en una función de hoja y RSP dirigirá directamente el puntero de devolución.  El puntero de devolución en \[RSP\] se almacena en el contexto actualizado, el RSP simulado se incrementa en 8 y se repite el paso 1.  
  
3.  Si se encuentra una entrada de tabla de la función, el valor de RIP puede estar en tres regiones: a\) en un epílogo, b\) en el prólogo, c\) en un código que puede estar cubierto por un controlador de excepciones.  
  
    -   Caso a\) Si el valor de RIP está en un epílogo, el control está abandonando la función, no puede haber un controlador de excepciones asociado a esta excepción para esta función y el efecto del epílogo debe continuar para calcular el contexto de la función llamadora.  Para determinar si el valor de RIP está dentro de un epílogo, se examina la secuencia de código a partir de RIP.  Si se puede hacer corresponder esta secuencia de código con la parte final de un epílogo legítimo, se encuentra en un epílogo y la parte restante de éste se simula, con el registro del contexto actualizado a medida que se procesa cada instrucción.  Después de esto, se repite el paso 1.  
  
    -   Caso b\) Si el valor de RIP está en el prólogo, el control no ha entrado en la función, no puede haber un controlador de excepciones asociado a esta excepción para esta función y el efecto del prólogo se debe deshacer para calcular el contexto de la función llamadora.  El valor de RIP está en el prólogo si la distancia desde el inicio de la función a RIP es menor o igual que el tamaño del prólogo codificado en la información de desenredo.  El efecto del prólogo se desenreda mediante examen hacia delante por la matriz de códigos de desenredo para la primera entrada con un desplazamiento menor o igual que el desplazamiento del valor de RIP desde el inicio de la función, y luego deshaciendo el efecto de todos los elementos restantes en la matriz de códigos de desenredo.  A continuación, se repite el paso 1.  
  
    -   Caso c\) Si el valor de RIP no está en el prólogo ni en un epílogo y la función tiene un controlador de excepciones \(UNW\_FLAG\_EHANDLER está establecido\), se llama al controlador específico del lenguaje.  El controlador examina sus datos y llama a funciones filtro según corresponda.  El controlador específico del lenguaje puede indicar que se controló la excepción o que la búsqueda debe continuar.  También puede iniciar un operación de desenredo directamente.  
  
4.  Si el controlador específico del lenguaje devuelve un estado controlado, la ejecución continúa utilizando el registro de contexto original.  
  
5.  Si no hay un controlador específico del lenguaje o el controlador devuelve un estado de "continuar la búsqueda", se debe desenredar el registro de contexto hasta el estado del llamador.  Esto se consigue procesando todos los elementos de la matriz de códigos de desenredo, deshaciendo el efecto de cada uno de ellos.  A continuación, se repite el paso 1.  
  
 Cuando hay información de desenredo encadenada implicada, también se siguen estos pasos básicos.  La única diferencia es que, mientras se recorre la matriz de códigos de desenredo para desenredar el efecto de un prólogo, una vez que se llega al final de la matriz, se establece un vínculo con la información de desenredo principal y se recorre la matriz de códigos de desenredo completa encontrada ahí.  Esta vinculación continúa hasta que se llega a una información de desenredo sin el marcador UNW\_CHAINED\_INFO y se termina de recorrer su matriz de códigos de desenredo.  
  
 El conjunto más pequeño de datos de desenredo es de 8 bytes.  Esto representaría una función que sólo asignó 128 bytes de pila o menos, y que posiblemente guardó un registro no variable.  También es el tamaño de una estructura de información de desenredo encadenada correspondiente a un prólogo de longitud cero sin códigos de desenredo.  
  
## Vea también  
 [Control de excepciones \(x64\)](../build/exception-handling-x64.md)