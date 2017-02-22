---
title: "Directivas de preprocesador | Microsoft Docs"
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
  - "directivas, preprocesador"
  - "preprocesador, directivas"
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Directivas de preprocesador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las directivas de preprocesador, tales como `#define` y **\#ifdef**, se utilizan normalmente para hacer que los programas de origen sean más fáciles de modificar y facilitar la compilación en diferentes entornos de ejecución.  Las directivas del archivo de código fuente indican al preprocesador que realice acciones específicas.  Por ejemplo, el preprocesador puede reemplazar tokens en el texto, insertar el contenido de otros archivos en el archivo de código fuente o suprimir la compilación de parte del archivo quitando secciones de texto.  Las líneas de preprocesador se reconocen y se ejecutan antes de la expansión de macro.  Por consiguiente, si una macro se expande en algo que se parezca a un comando de preprocesador, el preprocesador no reconocerá ese comando.  
  
 Las instrucciones de preprocesador utilizan el mismo juego de caracteres que las instrucciones del archivo de código fuente, con la excepción de que no se admiten secuencias de escape.  El juego de caracteres utilizado en las instrucciones de preprocesador es el mismo que el [juego de caracteres de la ejecución](http://msdn.microsoft.com/es-es/a7901c61-524d-47c6-beb6-d9dacc2e72ed).  El preprocesador también reconoce valores de caracteres negativos.  
  
 El preprocesador reconoce las siguientes directivas:  
  
|||||  
|-|-|-|-|  
|[\#define](../preprocessor/hash-define-directive-c-cpp.md)|[\#error](../preprocessor/hash-error-directive-c-cpp.md)|[\#import](../preprocessor/hash-import-directive-cpp.md)|[\#undef](../preprocessor/hash-undef-directive-c-cpp.md)|  
|[\#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#include](../preprocessor/hash-include-directive-c-cpp.md)|[\#using](../preprocessor/hash-using-directive-cpp.md)|  
|[\#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#line](../preprocessor/hash-line-directive-c-cpp.md)|[\#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|  
|[\#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||  
  
 El signo de número \(**\#**\) debe ser el primer carácter que no sea un carácter de espacio en blanco de la línea que contiene la directiva; pueden aparecer caracteres de espacio en blanco entre el signo de número y la primera letra de la directiva.  Algunas directivas incluyen argumentos o valores.  Cualquier texto que siga a una directiva \(excepto un argumento o un valor que forme parte de la directiva\) debe ir precedido por un delimitador de comentario de línea única \(**\/\/**\) o incluido entre delimitadores de comentario \(**\/\* \*\/**\).  Las líneas que contienen directivas de preprocesador se pueden continuar precediendo inmediatamente la marca de fin de línea con una barra diagonal inversa \(**\\**\).  
  
 Las directivas de preprocesador pueden aparecer en cualquier lugar de un archivo de código fuente, pero solo se aplican al resto del archivo de código fuente.  
  
## Vea también  
 [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)   
 [Macros predefinidas](../preprocessor/predefined-macros.md)   
 [Referencia del preprocesador de C\/C\+\+](../preprocessor/c-cpp-preprocessor-reference.md)