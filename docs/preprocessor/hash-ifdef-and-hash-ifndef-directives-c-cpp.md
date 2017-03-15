---
title: "#ifdef e #ifndef (Directivas) (C/C++) | Microsoft Docs"
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
  - "#ifndef"
  - "#ifdef"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#ifdef (directiva)"
  - "#ifndef (directiva)"
  - "ifdef (directiva) (#ifdef)"
  - "ifndef (directiva) (#ifndef)"
  - "preprocesador, directivas"
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #ifdef e #ifndef (Directivas) (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las directivas **\#ifdef** e **\#ifndef** realizan la misma tarea que la directiva `#if` cuando se utiliza con **defined**\( *identifier* \).  
  
## Sintaxis  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## Comentarios  
 Puede usar las directivas **\#ifdef** e **\#ifndef** en cualquier lugar donde se pueda utilizar `#if`.  La instrucción **\#ifdef** *identifier* es equivalente a `#if 1` cuando *identifier* se ha definido, y es equivalente a `#if 0` cuando *identifier* no se ha definido o no se ha definido con la directiva `#undef`.  Estas directivas solo comprueban la presencia o ausencia de identificadores definidos con `#define`, no comprueban los identificadores declarados en el código fuente de C o C\+\+.  
  
 Estas directivas se proporcionan únicamente por compatibilidad con las versiones anteriores del lenguaje.  Se prefiere la expresión constante **defined\(** *identifier* **\)** con la directiva `#if`.  
  
 La directiva **\#ifndef** comprueba lo contrario de la condición que comprueba **\#ifdef**.  Si el identificador no se ha definido \(o su definición se ha quitado con `#undef`\), la condición es true \(distinto de cero\).  De lo contrario, la condición es false \(0\).  
  
 **Específicos de Microsoft**  
  
 El elemento *identifier* se puede pasar desde la línea de comandos con la opción \/D.  Se pueden especificar hasta 30 macros con \/D.  
  
 Es útil para comprobar si existe una definición, porque una definición se puede pasar desde la línea de comandos.  Por ejemplo:  
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)