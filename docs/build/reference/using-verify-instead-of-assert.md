---
title: "Usar VERIFY en lugar de ASSERT | Microsoft Docs"
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
  - "assert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ASSERT (instrucciones)"
  - "aserciones, depurar"
  - "aserciones, solución de problemas en las instrucciones ASSERT"
  - "depurar [MFC], ASSERT (instrucciones)"
  - "depurar aserciones"
  - "VERIFY (macro)"
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar VERIFY en lugar de ASSERT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Supongamos que, al ejecutar la versión de depuración de la aplicación MFC, no se producen problemas.  Sin embargo, la versión de lanzamiento de la misma aplicación termina de forma anormal, devuelve resultados incorrectos o presenta algún otro comportamiento extraño.  
  
 Este problema puede surgir al colocar código importante en una instrucción ASSERT para comprobar si funciona correctamente.  Como las instrucciones ASSERT se marcan como comentarios en una versión de lanzamiento de un programa MFC, el código no funcionará correctamente.  
  
 Si está utilizando ASSERT para confirmar si una llamada a función se realizó correctamente, considere en su lugar el uso de [VERIFY](../Topic/VERIFY.md).  La macro VERIFY evalúa sus propios argumentos tanto en versiones de depuración como en versiones de lanzamiento de la aplicación.  
  
 Otra técnica recomendable consiste en asignar el valor devuelto por la función a una variable temporal y, a continuación, probar la variable en una instrucción ASSERT.  
  
 Examine el siguiente fragmento de código:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 Este código funciona perfectamente en una versión de depuración de una aplicación MFC.  Si la llamada a `calloc( )` no se realiza correctamente, aparece un mensaje de diagnóstico que indica el archivo y el número de línea.  Sin embargo, en una versión comercial de una aplicación MFC:  
  
-   La llamada a `calloc( )` no se produce nunca y `buf` queda sin inicializar, o bien  
  
-   `strcpy_s( )` copia “`Hello, World`” en una ubicación aleatoria de la memoria y, posiblemente, bloquea la aplicación, hace que el sistema deje de responder, o  
  
-   `free()` intenta liberar memoria que nunca se llegó a asignar.  
  
 Para utilizar ASSERT correctamente, el ejemplo de código se debería escribir del siguiente modo:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );  
ASSERT( buf != NULL );  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 O bien, puede utilizar VERIFY:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
## Vea también  
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)