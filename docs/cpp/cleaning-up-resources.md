---
title: "Limpiar recursos | Microsoft Docs"
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
helpviewer_keywords: 
  - "control de excepciones de C++, controladores de terminación"
  - "control de excepciones, limpiar recursos"
  - "control de excepciones, código de limpieza"
  - "recursos [C++], limpieza"
  - "controladores de terminación, limpiar recursos"
  - "try-catch (palabra clave) [C++], controladores de terminación"
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Limpiar recursos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Durante la ejecución del controlador de terminación, tal vez no sepa qué recursos se han asignado antes de que se llame al controlador de terminación.  Es posible que el bloque de instrucciones `__try` se interrumpiera antes de que se asignaran todos los recursos, de modo que no todos los recursos estuvieran abiertos.  
  
 Por tanto, como medida de seguridad, debe comprobar qué recursos están realmente abiertos antes de proceder con la limpieza de controladores de terminación.  Un procedimiento recomendado es:  
  
1.  Inicializar los identificadores en NULL.  
  
2.  En el bloque de instrucciones `__try`, asignar recursos.  Los identificadores se establecen en valores positivos cuando se asigna el recurso.  
  
3.  En el bloque de instrucciones `__finally`, liberar cada recurso cuyo identificador o variable de marca correspondiente sea distinto de cero o distinto de NULL.  
  
## Ejemplo  
 Por ejemplo, en el código siguiente se utiliza un controlador de terminación para cerrar tres archivos y un bloque de memoria asignados en el bloque de instrucciones `__try`.  Antes de limpiar un recurso, el código comprueba si el recurso se ha asignado.  
  
```  
// exceptions_Cleaning_up_Resources.cpp  
#include <stdlib.h>  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
  
void fileOps() {  
   FILE  *fp1 = NULL,  
         *fp2 = NULL,  
         *fp3 = NULL;  
   LPVOID lpvoid = NULL;  
   errno_t err;  
  
   __try {  
      lpvoid = malloc( BUFSIZ );  
  
      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );  
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );  
      err = fopen_s(&fp3, "CARS.DAT", "w+" );  
   }  
   __finally {  
      if ( fp1 )  
         fclose( fp1 );  
      if ( fp2 )  
         fclose( fp2 );  
      if ( fp3 )  
         fclose( fp3 );  
      if ( lpvoid )  
         free( lpvoid );  
   }  
}  
  
int main() {  
   fileOps();  
}  
```  
  
## Vea también  
 [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)   
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)