---
title: Gramática de preprocesador | Documentos de Microsoft
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
ms.openlocfilehash: d14a3e00e18a2d3ac69dd472ac4056a379ada224
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="preprocessor-grammar"></a>Gramática de preprocesador
**#define***identificador* *token-string*participar    
  
 *#* **definir***identificador*[**(** *identificador*opt **,** *...*  **,** *identificador*opt **)**] *token-string*participar    
  
 **define (***identificador* **)**   
  
 **define***identificador*  
  
 `#include` **"***especificación de ruta de acceso***"**  
  
 `#include` **\<***especificación de ruta de acceso***>**  
  
 **#line***secuencia de dígitos***"** *filename* **"** participar      
  
 *#* **undef***identificador*  
  
 **#error***cadena de token*   
  
 **#pragma***cadena de token*   
  
 *condicional* :  
 *partes de elif parte si*opt*parte else*opt*endif línea*  
  
 *parte de si* :  
 *If linetext*  
  
 *línea de IF* :  
 **#if***expresión constante*   
  
 **#ifdef***identificador*  
  
 **#ifndef***identificador*  
  
 *elif partes* :  
 *texto de la línea de elif*  
  
 *texto de línea elif elif partes*  
  
 *elif línea* :  
 **#elif***expresión constante*   
  
 *parte Else* :  
 *Else linetext*  
  
 *línea Else* :  
 `#else`  
  
 *endif línea* :  
 `#endif`  
  
 *secuencia de dígitos* :  
 *digit*  
  
 *digit-sequence digit*  
  
 *dígitos* : uno de  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *cadena de token* :  
 cadena de tokens  
  
 *símbolo (token)* :  
 *keyword*  
  
 *identifier*  
  
 *constant*  
  
 *operator*  
  
 `punctuator`  
  
 *nombre de archivo* :  
 nombre de archivo del sistema operativo válido  
  
 *especificación de ruta de acceso* :  
 Ruta de acceso válida  
  
 *texto* :  
 cualquier secuencia de texto  
  
> [!NOTE]
>  Los elementos no terminales siguientes se expanden en la [convenciones léxicas](../cpp/lexical-conventions.md) sección de la *referencia del lenguaje C++*: `constant`, `constant` - *expresión* , *identificador*, *palabra clave*, `operator`, y `punctuator`.  
  
## <a name="see-also"></a>Vea también  
 [Resumen de la gramática (C/C++)](../preprocessor/grammar-summary-c-cpp.md)