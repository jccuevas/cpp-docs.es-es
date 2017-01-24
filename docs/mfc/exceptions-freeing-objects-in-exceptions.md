---
title: "Excepciones: Liberar objetos en las excepciones | Microsoft Docs"
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
helpviewer_keywords: 
  - "destruir objetos"
  - "control de excepciones, destruir objetos"
  - "liberar objetos"
  - "control de excepciones locales"
  - "pérdidas de memoria, producido por excepción"
  - "producir excepciones, después de destruir"
  - "producir excepciones, liberar objetos en excepciones"
  - "control de excepciones try-catch, destruir objetos"
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Excepciones: Liberar objetos en las excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica la necesidad y el método de liberar objetos cuando se produce una excepción.  Entre los temas se incluyen los siguientes:  
  
-   [Administrar la excepción localmente](#_core_handling_the_exception_locally)  
  
-   [Excepciones después de eliminar objetos](#_core_throwing_exceptions_after_destroying_objects)  
  
 Las excepciones producidas por el marco o por la aplicación interrumpe el flujo normal del programa.  Por tanto, es muy importante mantener un seguimiento parecida a objetos para que se pueda eliminar correctamente de ellos en caso de que se produzca una excepción.  
  
 Hay dos métodos principales para ello.  
  
-   Controlan las excepciones localmente mediante las palabras clave de **try** y de **catch** , entonces se destruye todos los objetos con una instrucción.  
  
-   Destruya cualquier objeto en el bloque de **catch** antes de iniciar la excepción fuera del bloque para aún más administrar.  
  
 Estos dos enfoques se muestra debajo como soluciones al ejemplo problemático siguiente:  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 Escrita anteriormente, `myPerson` no se eliminará si una excepción se produce por `SomeFunc`.  La ejecución salta directamente al controlador de excepciones externo siguiente, omitiendo la salida de la función normal y el código que elimine el objeto.  El puntero al objeto salga del ámbito cuando la excepción sale de la función, y la memoria ocupada por el objeto nunca se recuperará mientras el programa se está ejecutando.  Esto es una pérdida de memoria; se detectaría mediante los diagnósticos de memoria.  
  
##  <a name="_core_handling_the_exception_locally"></a> Administrar la Excepción Locally  
 El ejemplo de **try\/catch** proporciona un método de programación estable para evitar pérdidas de memoria y asegurarse que los objetos se destruyeron cuando se produzcan excepciones.  Por ejemplo, el ejemplo mostrado anteriormente en este caso podría reescribir como sigue:  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 Este nuevo ejemplo prepara un controlador de excepciones para detectar la excepción y para controlarla localmente.  A continuación cierra la función normalmente y destruye el objeto.  Lo importante de este ejemplo es que un contexto para detectar la excepción está establecido con bloques try\/catch.  Sin un cuadro local de excepciones, la función nunca sabría que una excepción se hubiera produce y no tendrá la oportunidad de salir normalmente y de destruir el objeto.  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> Excepciones después de eliminar objetos  
 Otra manera de controlar excepciones es pasarlas al contexto externo siguiente de control de excepciones.  En el bloque de **catch** , puede hacer cualquier limpieza de objetos localmente asignados y después producir la excepción en para más procesamiento.  
  
 La función que produce puede o no puede necesitar desasignar objetos del montón.  Si la función desasigna siempre el objeto de pila antes de volver del caso normal, la función también debe desasignar el objeto de pila antes de iniciar la excepción.  Por otra parte, si la función no desasignó normalmente el objeto antes de volver del caso normal, debe decidir caso por caso si el objeto de pila se debe desasignar.  
  
 El ejemplo siguiente muestra cómo los objetos localmente asignados se pueden limpiar:  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 El mecanismo de excepción automáticamente desasigna objetos de cuadro; el destructor del objeto de marco también se denomina.  
  
 Si llama a las funciones que pueden producir excepciones, puede usar los bloques try\/catch para asegurarse de que detecta las excepciones y tiene una oportunidad de destruir cualquier objeto que haya creado.  En particular, tenga en cuenta que muchas funciones MFC pueden producir excepciones.  
  
 Para obtener más información, vea [Excepciones: Detectando y eliminar Excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)