---
title: '&lt;exception&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <exception>
dev_langs:
- C++
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbd57085225bb21b9f7ce8bd34c537d3bc414797
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

Define varios tipos y funciones relacionados con el control de excepciones. El control de excepciones se utiliza en aquellas situaciones en las que el sistema puede recuperarse de un error. Proporciona un medio para devolver el control de una función al programa. El objetivo de incorporar control de excepciones es aumentar la solidez del programa y proporcionar una manera de recuperarse de un error de forma ordenada.

## <a name="syntax"></a>Sintaxis

```cpp
#include <exception>

```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Tipo que describe un puntero a una excepción.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Tipo que describe un puntero a una función que se puede usar como `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Tipo que describe un puntero a una función que se puede usar como `unexpected_handler`.|

### <a name="functions"></a>Funciones

|Función|Descripción|
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

|Clase|Descripción|
|-|-|
|[bad_exception (Clase)](../standard-library/bad-exception-class.md)|La clase describe una excepción que se puede iniciar desde un `unexpected_handler`.|
|[exception (Clase)](../standard-library/exception-class.md)|La clase actúa como clase base para todas las excepciones iniciadas por determinadas expresiones y por la biblioteca estándar de C++.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
