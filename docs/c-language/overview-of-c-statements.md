---
title: "Información general sobre las instrucciones de C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 473a91651e52d04dbeb15301520c6c8984808551
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-c-statements"></a>Información general sobre las instrucciones de C
Las instrucciones de C se componen de tokens, expresiones y otras instrucciones. Una instrucción que forma un componente de otra instrucción se denomina el “cuerpo” de la instrucción de inclusión. En esta sección se analiza cada tipo de instrucción que se da con la sintaxis siguiente.  
  
## <a name="syntax"></a>Sintaxis  
 *statement*:  
 [labeled-statement](../c-language/goto-and-labeled-statements-c.md)  
  
 [compound-statement](../c-language/compound-statement-c.md)  
  
 [expression-statement](../c-language/expression-statement-c.md)  
  
 [selection-statement](../c-language/if-statement-c.md)  
  
 [iteration-statement](../c-language/do-while-statement-c.md)  
  
 [jump-statement](../c-language/break-statement-c.md)  
  
 [try-except-statement](../c-language/try-except-statement-c.md)  
  
 /* Específico de Microsoft \*/[try-finally-statement](../c-language/try-finally-statement-c.md) /\* Específico de Microsoft \*/  
  
 Con frecuencia, el cuerpo de la instrucción es una "instrucción compuesta". Una instrucción compuesta consta de otras instrucciones que pueden incluir palabras clave. La instrucción compuesta está delimitada por llaves (**{ }**). El resto de las instrucciones de C finalizan con un punto y coma (**;**). El punto y coma es un terminador de instrucciones.  
  
 La instrucción de expresión contiene una expresión de C que puede contener los operadores aritméticos o lógicos que se presentan en [Expresiones y asignaciones](../c-language/expressions-and-assignments.md). La instrucción nula es una instrucción vacía.  
  
 Cualquier instrucción de C puede empezar con una etiqueta identificativa que consta de un nombre y dos puntos. Como solo la instrucción `goto` reconoce etiquetas de instrucciones, las etiquetas de instrucciones se tratan con `goto`. Vea [Instrucciones goto y con etiquetas](../c-language/goto-and-labeled-statements-c.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones](../c-language/statements-c.md)