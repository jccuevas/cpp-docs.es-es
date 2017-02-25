---
title: "__if_not_exists (Instrucci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__if_not_exists"
  - "__if_not_exists_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__if_not_exists (palabra clave) [C++]"
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# __if_not_exists (Instrucci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La instrucción `__if_not_exists` prueba si existe el identificador especificado.  Si el identificador no existe, se ejecuta el bloque de instrucción especificado.  
  
## Sintaxis  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`identifier`|El identificador cuya existencia se desea probar.|  
|`statements`|Una o más instrucciones que se ejecutan si no existe `identifier` .|  
  
## Comentarios  
  
> [!CAUTION]
>  Para obtener los resultados más confiables, conviene utilizar la instrucción `__if_not_exists` con las restricciones siguientes.  
  
-   Aplique la instrucción `__if_not_exists` solo a tipos simples y no a plantillas.  
  
-   Aplique la instrucción `__if_not_exists` a identificadores tanto dentro como fuera de una clase.  No aplique la instrucción `__if_not_exists` a variables locales.  
  
-   Utilice la instrucción `__if_not_exists` solo en el cuerpo de una función.  Fuera del cuerpo de una función, la instrucción `__if_not_exists` solo puede probar tipos totalmente definidos.  
  
-   Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.  
  
 El complemento a la instrucción `__if_not_exists` es la instrucción [\_\_if\_exists](../cpp/if-exists-statement.md).  
  
## Ejemplo  
 Para obtener un ejemplo de cómo se usa `__if_not_exists`, vea [\_\_if\_exists \(Instrucción\)](../cpp/if-exists-statement.md).  
  
## Vea también  
 [Instrucciones de selección](../cpp/selection-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [\_\_if\_exists \(Instrucción\)](../cpp/if-exists-statement.md)