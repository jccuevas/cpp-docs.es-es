---
title: Gramática de preprocesador
ms.date: 09/04/2018
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: 17768b7ec1442f2af1abf76596527d4df69b1534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614193"
---
# <a name="preprocessor-grammar"></a>Gramática de preprocesador

*control de línea*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *identificador* *token-string*<sub>participar</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>identificador</em>**(** *identificador*<sub>opt</sub> **,** ... **,** *identificador*<sub>opt</sub> **)** *token-string*<sub>participar</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **"** *especificación de ruta* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *especificación de ruta de acceso* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *secuencia de dígitos***"** *filename* **"**<sub>participar</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *identificador*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *token-string*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *token-string*

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**define (** *identificador* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**define** *identificador*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;cualquier otra expresión constante

*condicional* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parte de si* *elif-partes*<sub>opt</sub> *parte else*<sub>opt</sub> *endif-línea*

*parte de si* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*If-línea* *texto*

*If-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *expresión constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *identificador*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *identificador*

*elif-partes* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-línea* *texto*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-partes* *elif-línea* *texto*

*elif-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *expresión constante*

*otro-parte* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*otro-línea* *texto*

*otro-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*secuencia de dígitos* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*dígitos* : uno de<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*cadena de token* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Cadena de tokens

*token* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*keyword*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*nombre de archivo* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Nombre de archivo del sistema operativo válido

*especificación de ruta* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Ruta de acceso válida

*texto* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Cualquier secuencia de texto

> [!NOTE]
> Los elementos no terminales siguientes se expanden en el [convenciones léxicas](../cpp/lexical-conventions.md) sección de la *referencia del lenguaje C++*: *constante*, *expresión constante* , *identificador*, *palabra clave*, *operador*, y *signo de puntuación*.

## <a name="see-also"></a>Vea también

[Resumen de la gramática (C/C++)](../preprocessor/grammar-summary-c-cpp.md)