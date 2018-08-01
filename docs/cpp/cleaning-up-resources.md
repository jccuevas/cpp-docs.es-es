---
title: Limpieza de recursos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c7c589f5ac6baef0ef4420d997fa6497f4e03d5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408740"
---
# <a name="cleaning-up-resources"></a>Limpiar recursos
Durante la ejecución del controlador de terminación, tal vez no sepa qué recursos se han asignado antes de que se llame al controlador de terminación. Es posible que el **__try** bloque de instrucciones se interrumpió antes de que todos los recursos asignados, por lo que no todos los recursos estuvieran abiertos.  
  
 Por tanto, como medida de seguridad, debe comprobar qué recursos están realmente abiertos antes de proceder con la limpieza de controladores de terminación. Un procedimiento recomendado es:  
  
1.  Inicializar los identificadores en NULL.  
  
2.  En el **__try** instrucción en bloques, asignar recursos. Los identificadores se establecen en valores positivos cuando se asigna el recurso.  
  
3.  En el **__finally** bloque de instrucciones, liberar cada recurso cuyo identificador correspondiente o la variable de indicador es distinto de cero o no NULL.  
  
## <a name="example"></a>Ejemplo  
 Por ejemplo, el código siguiente usa un controlador de terminación para cerrar tres archivos y un bloque de memoria que se asignaron durante la **__try** bloque de instrucciones. Antes de limpiar un recurso, el código comprueba si el recurso se ha asignado.  
  
```cpp 
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
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)   
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)