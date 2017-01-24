---
title: "Resoluci&#243;n de ambig&#252;edad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resoluci&#243;n de ambig&#252;edad
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para realizar conversiones explícitas de un tipo a otro, debe utilizar las conversiones especificando el nombre de tipo que desee.  Algunas conversiones de tipos producen ambigüedad sintáctica.  La siguiente conversión de tipo de estilo de función es ambigua:  
  
```  
char *aName( String( s ) );  
```  
  
 No queda claro si es una declaración de función o una declaración de objeto con una conversión de estilo de función como inicializador: podría declarar una función que devolviera el tipo **char \*** que toma un argumento de tipo `String` o podría declarar el argumento de objeto `aName` e inicializarlo con el valor de conversión `s` al tipo `String`.  
  
 Si una declaración puede considerarse una declaración de función válida, se trata como tal.  Solo si no puede ser una declaración de función \(es decir, si fuera sintácticamente incorrecta\) es una instrucción que podría tratarse como una conversión de tipo de estilo de función.  Por consiguiente, el compilador interpreta la instrucción como una declaración de una función y omite los paréntesis incluidos alrededor del identificador `s`.  Sin embargo, las instrucciones:  
  
```  
char *aName( (String)s );  
```  
  
 y  
  
```  
char *aName = String( s );  
```  
  
 son claramente declaraciones de objetos, y para realizar la inicialización de `aName` se llama a una conversión del tipo `String` al tipo **char \*** definida por el usuario.  
  
## Vea también  
 [C\+\+ Abstract Declarators](http://msdn.microsoft.com/es-es/e7e18c18-0cad-4450-942b-d27e1d4dd088)