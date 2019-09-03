---
title: Convenciones de documento
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, conventions
ms.assetid: 469ce448-dc6c-4d0e-ba2b-e2e7a10155e1
ms.openlocfilehash: bb826b879b71edd3631c11a717320cee51c87175
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220373"
---
# <a name="document-conventions"></a>Convenciones de documento

Las convenciones utilizan distintos atributos de fuente de diferentes componentes de la sintaxis. Los símbolos y fuentes son los siguientes:

| Atributo | DESCRIPCIÓN |
|---------------|-----------------|
| *elemento no terminal* | La cursiva indica elementos no terminales. |
| **#include** | Los elementos terminales en negrita son símbolos y palabras literales reservadas que deben especificarse tal como aparecen. Los caracteres en este contexto siempre distinguen entre mayúsculas y minúsculas. |
| <sub>opt</sub> | Los elementos no terminales seguidos de <sub>opt</sub> son siempre opcionales.|
| tipo de letra predeterminado | Los caracteres del juego descrito o mostrado en este tipo de letra se pueden usar como elementos terminales en las instrucciones. |

Un signo de dos puntos ( **:** ) a continuación de un no terminal presenta su definición. Las definiciones alternativas se indican en líneas distintas.

En los bloques de sintaxis de código, estos símbolos del tipo de letra predeterminado tienen un significado especial:

| Símbolo | DESCRIPCIÓN |
|---|---|
| \[ ] | Los corchetes rodean un elemento opcional. |
| { \| } | Las llaves rodean elementos alternativos, separados por barras verticales. |
| ... | Indica que el patrón de elemento anterior se puede repetir. |

En los bloques de sintaxis de código,`,`las comas (`.`), los puntos (),`;`los signos de punto y`:`coma (), los`( )`dos puntos (), los`"`paréntesis (), las comillas`'`dobles () y las comillas simples () son literales.

## <a name="see-also"></a>Vea también

[Resumen de la gramática (C++C/)](../preprocessor/grammar-summary-c-cpp.md)
