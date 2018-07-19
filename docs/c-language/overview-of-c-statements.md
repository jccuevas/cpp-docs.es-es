---
title: Información general sobre las instrucciones de C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3cf80e6237b21101f737f496eb39688ec6ed0a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387182"
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