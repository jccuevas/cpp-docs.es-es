---
title: "pointers_to_members | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pointers_to_members_CPP"
  - "vc-pragma.pointers_to_members"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "miembros de clases, punteros a"
  - "miembros, punteros a"
  - "pointers_to_members (pragma)"
  - "pragma (directivas), pointers_to_members"
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pointers_to_members
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica si un puntero a un miembro de una clase se puede declarar antes que su definición de clase asociada y se utiliza para controlar el tamaño de puntero y el código requerido para interpretar el puntero.  
  
## Sintaxis  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## Comentarios  
 Puede colocar una pragma **pointers\_to\_members** en el archivo de código fuente como alternativa al uso de las opciones de compilador [\/vmx](../build/reference/vmb-vmg-representation-method.md) o las [palabras clave de herencia](../cpp/inheritance-keywords.md).  
  
 El argumento *pointer\-declaration* especifica si se ha declarado un puntero a un miembro antes o después que la definición de función asociada.  El argumento *pointer\-declaration* es uno de los dos símbolos siguientes:  
  
|Argumento|Comentarios|  
|---------------|-----------------|  
|**full\_generality**|Genera código seguro, a veces no optimo.  Debe utilizar **full\_generality** si un puntero a un miembro se declara antes que la definición de clase asociada.  Este argumento siempre usa la representación de puntero especificada por el argumento *most\-general\-representation*.  Equivalente a \/vmg.|  
|**best\_case**|Genera código seguro y óptimo que usa la representación best\-case para todos los punteros a miembros.  Requiere que se defina la clase antes de declarar un puntero a un miembro de la clase.  El valor predeterminado es **best\_case**.|  
  
 El argumento *most\-general\-representation* especifica la representación más pequeña de puntero que el compilador puede utilizar de forma segura para hacer referencia a cualquier puntero a un miembro de una clase en una unidad de traducción.  El argumento puede ser uno de los siguientes:  
  
|Argumento|Comentarios|  
|---------------|-----------------|  
|**single\_inheritance**|La representación más general es single\-inheritance, puntero a una función miembro.  Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es múltiple o virtual.|  
|**multiple\_inheritance**|La representación más general es multiple\-inheritance, puntero a una función miembro.  Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es virtual.|  
|**virtual\_inheritance**|La representación más general es virtual\-inheritance, puntero a una función miembro.  Nunca produce un error.  Este es el argumento predeterminado cuando se utiliza **\#pragma pointers\_to\_members\(full\_generality\)**.|  
  
> [!CAUTION]
>  Se aconseja colocar la pragma `pointers_to_members` solo en el archivo de código fuente al que desea que afecte, y solo después de directivas `#include`.  Esta práctica reduce el riesgo de que la pragma afecte a otros archivos, y de que especifique accidentalmente varias definiciones para la misma variable, función o nombre de clase.  
  
## Ejemplo  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## Específicos de C\+\+: END  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)