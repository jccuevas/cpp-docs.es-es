---
title: "Option Strict On no permite conversiones impl&#237;cita de &#39;&lt;tipo1&gt;&#39; a &#39;&lt;tipo2&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30512"
  - "vbc30512"
helpviewer_keywords: 
  - "BC30512"
ms.assetid: b9756d48-05fa-4027-8a80-b4a0ef92099d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On no permite conversiones impl&#237;cita de &#39;&lt;tipo1&gt;&#39; a &#39;&lt;tipo2&gt;&#39;.
Intentó convertir un tipo en otro tipo que quizás no pueda contener el valor, como `Long` en `Integer`, mientras que el modificador de comprobación de tipo \([Option Strict \(Instrucción\)](../Topic/Option%20Strict%20Statement.md)\) está establecido en `On`.  
  
 Este tipo de conversión se denomina *conversión de restricción* y es posible que genere un error en tiempo de ejecución. Por este motivo, `Option Strict On` no permite conversiones de restricción implícitas.  
  
 **Identificador de error:** BC30512  
  
### Para corregir este error  
  
1.  Determine si existe una conversión de cualquier tipo de `<type1>` a `<type2>`. Si ambos son tipos elementales [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] o instancias de clases, esta determinación se puede realizar por lo general consultando la tabla de [Conversiones de ampliación y de restricción](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md).  
  
2.  Si solo existe una conversión de restricción de `<type1>` a `<type2>`, debe usar la conversión explícita. Las palabras clave [CType \(Función\)](../Topic/CType%20Function%20\(Visual%20Basic\).md) y [DirectCast \(Operador\)](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md) lanzan una excepción de tiempo de ejecución si se produce un error de conversión. La palabra clave [TryCast \(Operador\)](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md) solo se aplica a tipos de referencia y devuelve [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md) si se produce un error de conversión.  
  
3.  Si existe una conversión de restricción y el programa puede tolerar un error de tiempo de ejecución o está seguro de que un error de tiempo de ejecución no es posible, puede especificar `Option Strict Off` al principio del código fuente. No obstante, debe incluir la conversión en un bloque [Try...Catch...Finally \(Instrucción\)](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md) para evitar resultados inesperados o una finalización prematura del programa.  
  
4.  Si no existe ninguna conversión de `<type1>` a `<type2>`, debe volver a evaluar la lógica del programa. Es posible que pueda escribir código que pueda asignar valores a `<type2>` correspondientes a los valores anticipados de `<type1>`.  
  
5.  Si no existe ninguna conversión de `<type1>` a `<type2>` y uno de los tipos es una clase o estructura que ha definido, quizás pueda definir un operador de conversión a partir de ese tipo o del otro. Para obtener más información, consulta [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md).  
  
6.  En todos los casos y como norma general, debe evitar el uso de conversiones de restricción a menos que pueda interceptar errores en un bloque `Catch` y tratarlos de manera eficaz.  
  
## Vea también  
 [Option Strict \(Instrucción\)](../Topic/Option%20Strict%20Statement.md)   
 [Conversiones de ampliación y de restricción](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [CType \(Función\)](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [DirectCast \(Operador\)](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [TryCast \(Operador\)](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)   
 [Try...Catch...Finally \(Instrucción\)](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)