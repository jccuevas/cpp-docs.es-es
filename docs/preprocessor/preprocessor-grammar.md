---
title: Gramática de preprocesador
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: f0916e3cc9bbdb398db693286dacc4517df03557
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222260"
---
# <a name="preprocessor-grammar"></a>Gramática de preprocesador

*línea de control*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identificador* de *token-cadena* <sub>OPT</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identificador* de **(** &#x2800;identificador&#x200B;<sub>OPT</sub> **,** ... **,** *identificador* de &#x200B; <sub></sub>opt&#x2800; **)** *token: cadena*<sub>opcional</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _ruta de acceso: especificación_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** _ruta de acceso: especificación_ **\<** **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *digit-Sequence* **"** _nombre de archivo_ **"** &#x200B; <sub>OPT</sub>  \
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *identificador* de\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *token-cadena*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-cadena*

*Constant-Expression*: \
&nbsp;&nbsp;&nbsp;&nbsp;**definido (** &#x2800;*identificador*&#x2800; **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**definido** *identificador* de\
&nbsp;&nbsp;&nbsp;&nbsp;cualquier otra expresión constante

*condicional*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-part* *elif-parts*<sub>opt</sub> *else-part*<sub>opt</sub> *endif-line*

*si-parte*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-line* *text*

*If-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *expresión constante*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identificador* de\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identificador* de

*Elif-partes*: \
&nbsp;&nbsp;&nbsp;&nbsp;*Elif-línea* *texto* de\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-parts* *elif-line* *text*

*Elif-línea*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *expresión constante*

*else-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*else-line* *text*

*else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-línea*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*digit-Sequence*: \
&nbsp;&nbsp;&nbsp;&nbsp;*cifra*\
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*digit*: uno de \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*token-cadena*: \
&nbsp;&nbsp;&nbsp;&nbsp;Cadena de tokens

*token*: \
&nbsp;&nbsp;&nbsp;&nbsp;*palabra clave*\
&nbsp;&nbsp;&nbsp;&nbsp;*identificador*\
&nbsp;&nbsp;&nbsp;&nbsp;*constante*\
&nbsp;&nbsp;&nbsp;&nbsp;*Operator*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*nombre de archivo*: \
&nbsp;&nbsp;&nbsp;&nbsp;Nombre de archivo del sistema operativo legal

*ruta de acceso: especificación*: \
&nbsp;&nbsp;&nbsp;&nbsp;Ruta de acceso válida

*texto*: \
&nbsp;&nbsp;&nbsp;&nbsp;Cualquier secuencia de texto

> [!NOTE]
> Los siguientes elementos no terminales se expanden en la sección [convenciones léxicas](../cpp/lexical-conventions.md) de la  *C++ referencia del lenguaje*: *Constant*, *Constant-Expression*, *Identifier*, *Keyword*, *Operator*y  *signo de puntuación*.

## <a name="see-also"></a>Vea también

[Resumen de la gramática (C++C/)](../preprocessor/grammar-summary-c-cpp.md)
