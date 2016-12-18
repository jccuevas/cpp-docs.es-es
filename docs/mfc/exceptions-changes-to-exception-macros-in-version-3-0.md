---
title: "Excepciones: Cambios en las macros de excepci&#243;n en la versi&#243;n 3.0 | Microsoft Docs"
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
  - "control de excepciones de C++, consideraciones de actualización"
  - "CATCH (macro)"
  - "excepciones, cambios"
  - "THROW_LAST (macro)"
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Excepciones: Cambios en las macros de excepci&#243;n en la versi&#243;n 3.0
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Éste es un tema avanzado.  
  
 En la versión 3.0 de MFC y versiones posteriores, las macros de control de excepciones se han cambiado para utilizar excepciones de C\+\+.  Este artículo indica cómo esos cambios pueden afectar al comportamiento del código existente que utiliza las macros.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Tipos de excepción y la macro de CATCH](#_core_exception_types_and_the_catch_macro)  
  
-   [Excepciones Re\- que producen](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> Tipos de excepción y la macro de CATCH  
 En versiones anteriores de MFC, la información de tipo utilizada macro en tiempo de ejecución de **CATCH** MFC para determinar el tipo de excepción; determinan el tipo de excepción, es decir en el bloque catch.  Con las excepciones de C\+\+, sin embargo, el tipo del objeto de excepción determina el tipo de excepción siempre en el sitio de captura que se produce.  Esto producirá incompatibilidades en el caso poco frecuente donde el tipo de puntero al objeto iniciado difiere del tipo de objeto iniciado.  
  
 El ejemplo siguiente se muestra el resultado de esta diferencia entre la versión 3.0 de MFC y versiones anteriores:  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 Este código se comporta de manera diferente en la versión 3.0 porque el control pasa siempre en primer **catch** bloqueado con una excepción\- declaración coincidente.  El resultado de la expresión throw  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 se produce como **CException\***, aunque se genera como **CCustomException**.  La macro de **CATCH** en las versiones 2.5 de MFC y anterior utiliza `CObject::IsKindOf` para probar el tipo en tiempo de ejecución.  Dado que la expresión  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 es true, las primeras capturas del bloque catch la excepción.  En la versión 3.0, que utiliza las excepciones de C\+\+ para implementar muchas de las macros de control de excepciones, el segundo bloque catch coincide con `CException`system.typeloadexception.  
  
 El código siguiente es infrecuente.  Se produce normalmente cuando un objeto de excepción se pasa a otra función que acepta **CException\***genérico, realiza el procesamiento de “pre\- throw” y, finalmente produce una excepción.  
  
 Para evitar este problema, mover la expresión throw de la función al código de llamada y producir una excepción de tipo real conocido al compilador cuando se genera una excepción.  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> Excepciones Re\- que producen  
 Un bloque catch no puede producir el mismo puntero de la excepción que cogió.  
  
 Por ejemplo, este código era válido en las versiones anteriores, pero tendrá resultados inesperados con la versión 3.0:  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 Mediante **THROW** en el bloque catch hace que el puntero `e` que se va a eliminar, de modo que el sitio externo de captura recibe un puntero no válido.  Uso `THROW_LAST` al re\- captura `e`.  
  
 Para obtener más información, vea [Excepciones: Detectando y eliminar Excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)