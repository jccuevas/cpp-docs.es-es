---
title: "result_of (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "result_of"
  - "std.result_of"
  - "std::result_of"
  - "type_traits/std::result_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "result_of"
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# result_of (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Determina el tipo de valor devuelto del tipo que se puede llamar que toma los tipos de argumento especificados.  
  
## Sintaxis  
  
```  
template <class Fn, class... ArgTypes>  
    struct result_of<Fn(ArgTypes...)>;  
```  
  
#### Parámetros  
 `Fn`  
 El tipo que se puede llamar a la consulta.  
  
 `ArgTypes`  
 Los tipos de la lista de argumentos para el tipo que se puede llamar a la consulta.  
  
## Comentarios  
 Utilice esta plantilla para determinar en tiempo de compilación, el tipo de resultado de `Fn`\(`ArgTypes`\), donde `Fn` es un tipo que se puede llamar invocado con una lista de argumentos de los tipos de `ArgTypes`. El `type` el tipo de resultado de los nombres de miembro de la clase de plantilla `decltype(INVOKE(declval<Fn>(), declval<ArgTypes>()...))` Si la expresión no evaluada `INVOKE(declval<Fn>(), declval<ArgTypes>()...)` es correcto. De lo contrario, la clase de plantilla no tiene ningún miembro `type`. El tipo `Fn` y todos los tipos en el módulo del parámetro `ArgTypes` debe ser de tipos completos, `void`, o matrices de límite desconocido.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)