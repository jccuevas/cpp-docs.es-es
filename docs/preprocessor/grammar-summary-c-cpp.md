---
title: Resumen de la gramática del preprocesador (C/C++)
description: Define y describe la sintaxis de gramáticaC++ del preprocesador de Microsoft C/Compiler (MSVC).
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 68e5f09acfc6444afb46bcbc0f7e9db10b04afed
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076872"
---
# <a name="preprocessor-grammar-summary-cc"></a>Resumen de la gramática del preprocesador (C/C++)

En este artículo se describe la gramática formal de C C++ y el preprocesador. Trata la sintaxis de las directivas y los operadores de preprocesamiento. Para obtener más información, vea directivas de [preprocesador](../preprocessor/preprocessor.md) y [pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="definitions-for-the-grammar-summary"></a><a name="definitions"></a>Definiciones del Resumen de la gramática

Los elementos terminales son puntos de conexión en una definición de sintaxis. No hay ninguna otra posible resolución. Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.

Los elementos no terminales son marcadores en la sintaxis. La mayoría se definen en otro lugar en este resumen de la sintaxis. Las definiciones pueden ser recursivas. Los siguientes elementos no terminales se definen en la sección [convenciones léxicas](../cpp/lexical-conventions.md) de la  *C++ referencia del lenguaje*:

*constante*, *constante-expresión*, *identificador*, *palabra clave*, *operador*, *signo de puntuación*

Un componente opcional se indica mediante el subíndice <sub>opt</sub>. Por ejemplo, la sintaxis siguiente indica una expresión opcional encerrada entre llaves:

**{** *expresión*<sub>OPT</sub> **}**

## <a name="document-conventions"></a><a name="conventions"></a>Convenciones de documento

Las convenciones utilizan distintos atributos de fuente de diferentes componentes de la sintaxis. Los símbolos y fuentes son los siguientes:

| Atributo | Descripción |
|---------------|-----------------|
| *elemento no terminal* | La cursiva indica elementos no terminales. |
| **#include** | Los elementos terminales en negrita son símbolos y palabras literales reservadas que deben especificarse tal como aparecen. Los caracteres en este contexto siempre distinguen entre mayúsculas y minúsculas. |
| <sub>opt</sub> | Los elementos no terminales seguidos de <sub>opt</sub> son siempre opcionales.|
| tipo de letra predeterminado | Los caracteres del juego descrito o mostrado en este tipo de letra se pueden usar como elementos terminales en las instrucciones. |

Un signo de dos puntos ( **:** ) a continuación de un no terminal presenta su definición. Las definiciones alternativas se indican en líneas distintas.

En los bloques de sintaxis de código, estos símbolos del tipo de letra predeterminado tienen un significado especial:

| Símbolo | Descripción |
|---|---|
| \[ ] | Los corchetes rodean un elemento opcional. |
| {\|} | Las llaves rodean elementos alternativos, separados por barras verticales. |
| … | Indica que el patrón de elemento anterior se puede repetir. |

En los bloques de sintaxis de código, las comas (`,`), los puntos (`.`), los puntos y coma (`;`), los dos puntos (`:`), los paréntesis (`( )`), las comillas dobles (`"`) y las comillas simples (`'`) son literales.

## <a name="preprocessor-grammar"></a><a name="grammar"></a>Gramática del preprocesador

*línea de control*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identifier* *token de identificador-cadena*<sub>OPT</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identificador* de #define **(** *identificador*<sub>OPT</sub> **,** ... **,** *Identifier*<sub>OPT</sub> **)** *token-String*<sub>OPT</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _rutaDeAcceso-Spec_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<** _rutaDeAcceso-Spec_ **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *secuencia* **"** _filename_ **"** <sub>OPT</sub>\
&nbsp;&nbsp; **&nbsp;&nbsp;** *identificador* #undef\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *cadena de token*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *cadena de token*

*Constant-Expression*: \
&nbsp;&nbsp;&nbsp;&nbsp;**definido (** *identificador* **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**defined** *identificador* definido\
&nbsp;&nbsp;&nbsp;&nbsp;cualquier otra expresión constante

*condicional*: \
&nbsp;&nbsp;&nbsp;&nbsp;*si-parte* *Elif-* Parts<sub>OPC</sub> *else-Part*<sub>OPC</sub> *endif-line*

*si-parte*: \
&nbsp;&nbsp;&nbsp;&nbsp;*texto* *If-line*

*If-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *expresión constante*\
&nbsp;&nbsp; **&nbsp;&nbsp;** *identificador* #ifdef\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identificador* de #ifndef

*Elif-partes*: \
&nbsp;&nbsp;&nbsp;&nbsp;*texto* *de línea Elif*\
&nbsp;&nbsp;&nbsp;&nbsp;*texto* *de la línea* Elif de *partes Elif*

*Elif-línea*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *expresión constante*

*else-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*texto* *de la línea adicional*

*else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-línea*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*digit-Sequence*: \
&nbsp;&nbsp;&nbsp;&nbsp;*dígito*\
&nbsp;&nbsp;&nbsp;&nbsp;digit *-Sequence* *digit*

*digit*: uno de \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*token-cadena*: \
&nbsp;&nbsp;&nbsp;&nbsp;cadena de tokens

*token*: \
&nbsp;&nbsp;&nbsp;*palabra clave* &nbsp;\
&nbsp;&nbsp;&nbsp;*identificador* &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*constante*\
&nbsp;&nbsp;&nbsp;&nbsp;*operador*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*nombre de archivo*: \
&nbsp;&nbsp;&nbsp;&nbsp;nombre de archivo del sistema operativo legal

*ruta de acceso: especificación*: \
&nbsp;&nbsp;&nbsp;&nbsp;Ruta de acceso válida

*texto*: \
&nbsp;&nbsp;&nbsp;&nbsp;cualquier secuencia de texto

> [!NOTE]
> Los siguientes elementos no terminales se expanden en la sección [convenciones léxicas](../cpp/lexical-conventions.md) de la  *C++ referencia del lenguaje*: *constante*, *constante-expresión*, *identificador*, *palabra clave*, *operador*y *signo de puntuación*.

## <a name="see-also"></a>Consulte también

[Referencia deC++ C/preprocesador](../preprocessor/c-cpp-preprocessor-reference.md)
