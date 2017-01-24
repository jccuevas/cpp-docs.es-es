---
title: "&lt;exception&gt; | Microsoft Docs"
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
  - "<exception>"
  - "std::<exception>"
  - "std.<exception>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exception (encabezado)"
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;exception&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varios tipos y funciones relacionados con el control de excepciones. El control de excepciones se utiliza en aquellas situaciones en las que el sistema puede recuperarse de un error. Proporciona un medio para devolver el control de una función al programa. El objetivo de incorporar control de excepciones es aumentar la solidez del programa y proporcionar una manera de recuperarse de un error de forma ordenada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <exception>  
  
```  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[exception_ptr](../Topic/%3Cexception%3E%20typedefs.md#exception_ptr)|Tipo que describe un puntero a una excepción.|  
|[terminate_handler](../Topic/%3Cexception%3E%20typedefs.md#terminate_handler)|Tipo que describe un puntero a una función que se puede usar como `terminate_handler`.|  
|[unexpected_handler](../Topic/%3Cexception%3E%20typedefs.md#unexpected_handler)|Tipo que describe un puntero a una función que se puede usar como `unexpected_handler`.|  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[current_exception](../Topic/%3Cexception%3E%20functions.md#current_exception)|Obtiene un puntero a la excepción actual.|  
|[get_terminate](../Topic/%3Cexception%3E%20functions.md#get_terminate)|Obtiene la función `terminate_handler` actual.|  
|[get_unexpected](../Topic/%3Cexception%3E%20functions.md#get_unexpected)|Obtiene la función `unexpected_handler` actual.|  
|[make_exception_ptr](../Topic/%3Cexception%3E%20functions.md#make_exception_ptr)|Crea un objeto `exception_ptr` que contiene una copia de una excepción.|  
|[rethrow_exception](../Topic/%3Cexception%3E%20functions.md#rethrow_exception)|Inicia una excepción pasada como parámetro.|  
|[set_terminate](../Topic/%3Cexception%3E%20functions.md#set_terminate)|Establece un nuevo `terminate_handler` al que se llamará cuando finalice el programa.|  
|[set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected)|Establece un nuevo `unexpected_handler` cuando se encuentra una excepción inesperada.|  
|[Finalizar](../Topic/%3Cexception%3E%20functions.md#terminate)|Llama a un controlador de finalización.|  
|[uncaught_exception](../Topic/%3Cexception%3E%20functions.md#uncaught_exception)|Devuelve **true** solo si se está procesando actualmente una excepción producida.|  
|[inesperado](../Topic/%3Cexception%3E%20functions.md#unexpected)|Llama a un controlador inesperado.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[Clase bad_exception](../standard-library/bad-exception-class.md)|La clase describe una excepción que se puede iniciar desde un `unexpected_handler`.|  
|[Clase Exception](Exception%20Class.xml)|La clase actúa como clase base para todas las excepciones iniciadas por determinadas expresiones y por la biblioteca estándar de C++.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

