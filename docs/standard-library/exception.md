---
title: '&lt;exception&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <exception>
dev_langs: C++
helpviewer_keywords: exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a7624e80138e2c7feb77b9aa385a40a2b5fe0320
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;
Define varios tipos y funciones relacionados con el control de excepciones. El control de excepciones se utiliza en aquellas situaciones en las que el sistema puede recuperarse de un error. Proporciona un medio para devolver el control de una función al programa. El objetivo de incorporar control de excepciones es aumentar la solidez del programa y proporcionar una manera de recuperarse de un error de forma ordenada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <exception>  
  
```  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Tipo que describe un puntero a una excepción.|  
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Tipo que describe un puntero a una función que se puede usar como `terminate_handler`.|  
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Tipo que describe un puntero a una función que se puede usar como `unexpected_handler`.|  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[current_exception](../standard-library/exception-functions.md#current_exception)|Obtiene un puntero a la excepción actual.|  
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Obtiene la función `terminate_handler` actual.|  
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Obtiene la función `unexpected_handler` actual.|  
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Crea un objeto `exception_ptr` que contiene una copia de una excepción.|  
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Inicia una excepción pasada como parámetro.|  
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Establece un nuevo `terminate_handler` al que se llamará cuando finalice el programa.|  
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Establece un nuevo `unexpected_handler` cuando se encuentra una excepción inesperada.|  
|[terminate](../standard-library/exception-functions.md#terminate)|Llama a un controlador de finalización.|  
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Devuelve **True** solo si se está procesando actualmente una excepción iniciada.|  
|[unexpected](../standard-library/exception-functions.md#unexpected)|Llama a un controlador inesperado.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[bad_exception (Clase)](../standard-library/bad-exception-class.md)|La clase describe una excepción que se puede iniciar desde un `unexpected_handler`.|  
|[exception (Clase)](../standard-library/exception-class.md)|La clase actúa como clase base para todas las excepciones iniciadas por determinadas expresiones y por la biblioteca estándar de C++.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

