---
title: "Cuerpo de funci&#243;n | Microsoft Docs"
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
helpviewer_keywords: 
  - "cuerpo de función"
  - "definiciones de funciones, cuerpo de función"
  - "funciones [C], sintaxis"
  - "variables, sintaxis de función"
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Cuerpo de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un "cuerpo de función" es una instrucción compuesta que contiene instrucciones que especifican lo que hace la función.  
  
## Sintaxis  
 *function\-definition*:  
 *declaration\-specifiers*  opt *attribute\-seq* opt *declarator declaration\-list* opt *compound\-statement*  
  
 \/\* *attribute\-seq* es específico de Microsoft \*\/  
  
 *compound\-statement*: \/\* cuerpo de la función \/\*  
 **{**  *declaration\-list*  opt *statement\-list* opt **}**  
  
 Las variables declaradas en el cuerpo de función, o "variables locales", tienen clase de almacenamiento **auto** a menos que se especifique lo contrario.  Cuando se llama a la función, se crea el almacenamiento para las variables locales y se realizan las inicializaciones locales.  El control de ejecución pasa a la primera instrucción de *compound\-statement* y continúa hasta que se ejecuta una instrucción `return` o hasta que se encuentra el final del cuerpo de función.  A continuación, el control se devuelve al punto en el que se llamó a la función.  
  
 Una instrucción `return` que contiene una expresión debe ejecutarse si la función tiene que devolver un valor.  El valor devuelto de una función es indefinido si no se ejecuta ninguna instrucción `return` o si la instrucción `return` no incluye una expresión.  
  
## Vea también  
 [Definiciones de funciones de C](../c-language/c-function-definitions.md)