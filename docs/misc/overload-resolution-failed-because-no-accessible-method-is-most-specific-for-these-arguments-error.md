---
title: "Se produjo un error de resoluci&#243;n de sobrecarga porque ning&#250;n &#39;&lt;m&#233;todo&gt;&#39; accesible es m&#225;s espec&#237;fico para estos argumentos: &lt;error&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "error de resolución"
  - "BC30521"
  - "Error en la resolución de sobrecarga"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se produjo un error de resoluci&#243;n de sobrecarga porque ning&#250;n &#39;&lt;m&#233;todo&gt;&#39; accesible es m&#225;s espec&#237;fico para estos argumentos: &lt;error&gt;
Realizó una llamada a un método sobrecargado, pero el compilador encontró dos o más sobrecargas con listas de parámetros a los que se puede convertir la lista de argumentos y no puede seleccionar entre estas.  
  
 El compilador intenta que los tipos de datos en la lista de argumentos de llamada y la lista de parámetros de sobrecarga coincidan lo máximo posible. Requiere una conversión de ampliación de cada uno de los argumentos al parámetro correspondiente, tanto si el modificador de comprobación de tipo \([Option Strict \(Instrucción\)](../Topic/Option%20Strict%20Statement.md)\) es `On` como si es `Off`.  
  
 Si el compilador encuentra más de una sobrecarga que satisface el requisito de ampliación, busca la sobrecarga que es más específica para los tipos de datos del argumento, es decir, que realiza una llamada para la menor cantidad de ampliación. Genera este mensaje de error cuando una sobrecarga es más específica para el tipo de datos de un argumento, mientras que otra sobrecarga es más específica para el tipo de datos de otro argumento. Para obtener más información y un ejemplo, vea [Resolución de sobrecargas](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md).  
  
 **Identificador de error:** BC30521  
  
### Para corregir este error  
  
1.  Revise todas las sobrecargas del método y determine a cuál desea llamar.  
  
2.  En la instrucción de llamada, haga que los tipos de datos de los argumentos coincidan con los tipos de datos de los parámetros definidos para la sobrecarga deseada. Es posible que deba usar la [CType \(Función\)](../Topic/CType%20Function%20\(Visual%20Basic\).md) para convertir uno o más tipos de datos a los tipos definidos.  
  
## Vea también  
 [Sobrecarga de procedimientos](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Consideraciones sobre la sobrecarga de procedimientos](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)   
 [Resolución de sobrecargas](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Propiedades y métodos sobrecargados](../Topic/Overloaded%20Properties%20and%20Methods%20\(Visual%20Basic\).md)   
 [Option Strict \(Instrucción\)](../Topic/Option%20Strict%20Statement.md)   
 [CType \(Función\)](../Topic/CType%20Function%20\(Visual%20Basic\).md)