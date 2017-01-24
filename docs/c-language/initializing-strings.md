---
title: "Inicializar cadenas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "matrices de caracteres, inicializar"
  - "inicializar matrices, cadenas"
  - "cadenas [C++], inicializar"
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Inicializar cadenas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede inicializar una matriz de caracteres \(o caracteres anchos\) con un literal de cadena \(o literal de cadena ancho\).  Por ejemplo:  
  
```  
char code[ ] = "abc";  
```  
  
 inicializa `code` como una matriz de caracteres de cuatro elementos.  El cuarto elemento es el carácter null, que finaliza todos los literales de cadena.  
  
 La longitud de una lista de identificadores solo puede equivaler al número de identificadores que se inicializarán.  Si especifica un tamaño de matriz que es más corto que la cadena, se omiten los caracteres adicionales.  Por ejemplo, la declaración siguiente inicializa `code` como una matriz de caracteres de tres elementos:  
  
```  
char code[3] = "abcd";  
```  
  
 Solo los tres primeros caracteres del inicializador se asignan a `code`.  Se descartan el carácter `d` y el carácter null que finaliza la cadena.  Observe que se crea una cadena no finalizada \(es decir, una cadena que carece de un valor 0 que indique su final\) y genera un mensaje de diagnóstico para notificar esta condición.  
  
 La declaración  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 es idéntica a  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 Si el tamaño de la cadena es menor que el especificado de la matriz, los elementos restantes de la matriz se inicializan en 0.  
  
 **Específicos de Microsoft**  
  
 En Microsoft C, los literales de cadena pueden tener hasta 2048 bytes de longitud.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Inicialización](../c-language/initialization.md)