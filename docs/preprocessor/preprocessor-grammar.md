---
title: "Gramática de preprocesador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02b3597b035e3ea4bfa1670aa405109f4c01a077
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="preprocessor-grammar"></a>Gramática de preprocesador
**#define**  *identifier* *token-string*opt  
  
 *#* **define**  *identifier*[**(** *identifier*opt**,** *...* **,** *identifier*opt **)**] *token-string*opt  
  
 **defined(**  *identifier* **)**  
  
 **define***identificador*   
  
 `#include` **"***path-spec***"**  
  
 `#include` **\<***path-spec***>**  
  
 **#line**  *digit-sequence*  **"** *filename* **"**opt  
  
 *#* **undef***identificador*   
  
 **#error**  *token-string*  
  
 **#pragma**  *token-string*  
  
 *condicional* :  
 *partes de elif parte si*opt*parte else*opt*endif línea*  
  
 *parte de si* :  
 *if-linetext*  
  
 *línea de IF* :  
 **#if**  *constant-expression*  
  
 **#ifdef***identificador*  
  
 **#ifndef***identificador*  
  
 *elif partes* :  
 *texto de la línea de elif*  
  
 *texto de línea elif elif partes*  
  
 *elif línea* :  
 **#elif**  *constant-expression*  
  
 *else-part* :  
 *else-linetext*  
  
 *línea Else* :  
 `#else`  
  
 *endif línea* :  
 `#endif`  
  
 *digit-sequence* :  
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