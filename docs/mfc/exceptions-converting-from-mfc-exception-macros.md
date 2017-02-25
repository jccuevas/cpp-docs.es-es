---
title: "Excepciones: Convertir desde macros de excepciones de MFC | Microsoft Docs"
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
  - "bloques catch, delimitar"
  - "CException (clase), eliminar objetos de clase CException"
  - "conversiones, código escrito con macros MFC"
  - "convertir excepciones"
  - "control de excepciones, convertir excepciones"
  - "objetos de excepción"
  - "objetos de excepción, eliminar"
  - "excepciones, convertir"
  - "excepciones, eliminar objetos de excepción"
  - "palabras clave [C++], macros"
  - "macros, palabras clave de C++"
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Excepciones: Convertir desde macros de excepciones de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Éste es un tema avanzado.  
  
 En este artículo se explica cómo convertir el código existente escrito con macros de la clase de la Microsoft foundation class — **TRY**, **CATCH**, **THROW**, etc.\) para utilizar las palabras clave **try**, **catch**, y `throw`de control de excepciones de C\+\+.  Entre los temas se incluyen los siguientes:  
  
-   [Ventajas de conversión](#_core_advantages_of_converting)  
  
-   [Convertir código con macros de excepción para utilizar excepciones de C\+\+](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> Ventajas de convertir  
 No necesita probablemente convertir código existente, aunque se debe tener en cuenta las diferencias entre las implementaciones de macro en la versión 3.0 de MFC y las implementaciones en versiones anteriores.  Estas diferencias y cambios subsiguientes del comportamiento del se tratan en [Excepciones: Cambios en las macros de Excepciones en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
 Las ventajas principales de convertir son:  
  
-   El código que utiliza las palabras clave de control de excepciones de C\+\+ compila un archivo .EXE o un .DLL ligeramente más pequeño.  
  
-   Las palabras clave de control de excepciones de C\+\+ son más versátiles: Pueden controlar las excepciones de cualquier tipo de datos que se pueden copiar \(`int`, **flotante**, `char`, etc.\), mientras que las macros controlan excepciones sólo de la clase `CException` y las clases derivadas de ella.  
  
 La diferencia principal entre macros de y las palabras clave es que el código mediante las macros “automáticamente” elimina una excepción detectada cuando la excepción sale del ámbito.  El código mediante las palabras clave no lo hace, por lo que debe eliminar explícitamente una excepción detectada.  Para obtener más información, vea el artículo [Excepciones: Detectando y eliminar Excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Otra diferencia es sintaxis.  La sintaxis para las macros y las palabras clave diferencia en tres aspectos:  
  
1.  Argumentos de macros y declaraciones de excepción:  
  
     Una llamada de macro de **CATCH** tiene la siguiente sintaxis:  
  
     *Exception\_class de* **CATCH\(**, *exception\_object\_pointer\_name* \#\#\#\)  
  
     Observe la coma entre el nombre de clase y el nombre del puntero de objeto.  
  
     La declaración de excepción para la palabra clave de **catch** utiliza esta sintaxis:  
  
     *exception\_name* \#\#\#\)*de exception\_type*de**catch\(**  
  
     Esta instrucción de declaración de excepción indica el tipo de excepción el bloque catch.  
  
2.  Delimitador de bloques catch:  
  
     Con las macros, la macro de **CATCH** \(con sus argumentos\) inicia el primer bloque catch; los bloques catch subsiguientes de comienza de la macro de `AND_CATCH` , y la macro de `END_CATCH` finaliza la secuencia de bloques catch.  
  
     Con las palabras clave, la palabra clave de **catch** \(con su declaración de excepción\) inicia cada bloque catch.  No hay equivalente a la macro de `END_CATCH` ; finaliza el bloque catch con la llave de cierre.  
  
3.  La expresión throw:  
  
     Las macros utilizan el re\- captura de `THROW_LAST` la excepción actual.  La palabra clave de `throw` , sin el argumento, tiene el mismo efecto.  
  
##  <a name="_core_doing_the_conversion"></a> Hacer la conversión  
  
#### Para convertir código mediante macros para utilizar las palabras clave de control de excepciones de C\+\+  
  
1.  Busque todas las apariciones de macros **TRY**, **CATCH**, `AND_CATCH`, `END_CATCH`, **THROW**, y `THROW_LAST`MFC.  
  
2.  Reemplace o elimine todas las apariciones de macros siguientes:  
  
     **TRY** \(Sustitúyalo por **try**\)  
  
     **CATCH** \(Sustitúyalo por **catch**\)  
  
     `AND_CATCH` \(sustitúyalo por **catch**\)  
  
     `END_CATCH` \(Suprimir él\)  
  
     **THROW** \(Sustitúyalo por `throw`\)  
  
     `THROW_LAST` \(sustitúyalo por `throw`\)  
  
3.  Modifique los argumentos de macros de modo que constituyen declaraciones válidas de la excepción.  
  
     Por ejemplo, cambie  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     por  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  Modifique el código de los bloques catch de para que quite objetos de excepción según sea necesario.  Para obtener más información, vea el artículo [Excepciones: Detectando y eliminar Excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 A continuación se muestra un ejemplo del código de control de excepciones con macros de excepción de MFC.  Dado que el código del ejemplo siguiente utiliza las macros, la excepción `e` se elimina automáticamente:  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 El código del ejemplo siguiente utiliza las palabras clave de excepciones de C\+\+, por lo que la excepción debe explícitamente eliminarse:  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 Para obtener más información, vea [Excepciones: Utilizando las macros y C\+\+ Excepciones de MFC](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)