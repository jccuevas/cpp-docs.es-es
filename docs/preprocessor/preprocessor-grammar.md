---
title: Gramática de preprocesador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1871d1b8281f4dd74733133ede70ed80430246b3
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539287"
---
# <a name="preprocessor-grammar"></a>Gramática de preprocesador
**#define***identificador* *token-string*participar    
  
*#* **definir***identificador*[**(** *identificador*opt **,** *...*  **,** *identificador*opt **)**] *token-string*participar    
  
**define (***identificador* **)**   
  
**define***identificador*   
  
`#include` **"***especificación de ruta***"**  
  
`#include` **\<***especificación de ruta de acceso***>**  
  
**#line***secuencia de dígitos***"** *filename* **"** participar      
  
*#* **undef***identificador*   
  
**#error***token-string*   
  
**#pragma***token-string*   
  
*condicional* :  
*elif-partes de la parte de si*opt*parte else*opt*endif-línea*  
  
*parte de si* :  
*If linetext*  
  
*If-línea* :  
**#if***expresión constante*  
  
**#ifdef***identificador*  
  
**#ifndef***identificador*  
  
*elif-partes* :  
*texto elif-línea*  
  
*texto de elif-partes elif-línea*  
  
*elif-línea* :  
**#elif***expresión constante*  
  
*otro-parte* :  
*Else linetext*  
  
*otro-línea* :  
`#else`  
  
*endif-línea* :  
`#endif`  
  
*secuencia de dígitos* :  
*digit*  
  
*digit-sequence digit*  
  
*dígitos* : uno de  
**0 1 2 3 4 5 6 7 8 9**  
  
*cadena de token* :  
cadena de tokens  
  
*token* :  
*keyword*  
  
*identifier*  
  
*constant*  
  
*operator*  
  
`punctuator`  
  
*nombre de archivo* :  
nombre de archivo del sistema operativo válido  
  
*especificación de ruta* :  
Ruta de acceso válida  
  
*texto* :  
cualquier secuencia de texto  
  
> [!NOTE]
> Los elementos no terminales siguientes se expanden en el [convenciones léxicas](../cpp/lexical-conventions.md) sección de la *referencia del lenguaje C++*: `constant`, `constant` - *expresión* , *identificador*, *palabra clave*, `operator`, y `punctuator`.  
  
## <a name="see-also"></a>Vea también  
 
[Resumen de la gramática (C/C++)](../preprocessor/grammar-summary-c-cpp.md)