---
title: Longitud máxima de cadena
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: f2e5461c433a0d195682c1a0f4312a71a8ff5032
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483991"
---
# <a name="maximum-string-length"></a>Longitud máxima de cadena

**Específicos de Microsoft**

La compatibilidad con ANSI requiere que un compilador acepte hasta 509 caracteres en un literal de cadena después de la concatenación. La longitud máxima de un literal de cadena permitida en Microsoft C es aproximadamente 2.048 bytes. Sin embargo, si el literal de cadena consta de partes incluidas entre comillas dobles, el preprocesador concatena las partes en una sola cadena, y para cada línea concatenada, agrega un byte adicional al número total de bytes.

Por ejemplo, suponga que una cadena consta de 40 líneas con 50 caracteres por línea (2.000 caracteres) y una línea con 7 caracteres, y cada línea está incluida entre comillas dobles. Esto agrega hasta 2.007 bytes más un byte por carácter null de finalización, para un total de 2.008 bytes. En la concatenación, se agrega un carácter adicional por cada una de las 40 primeras líneas. Esto hace un total de 2.048 bytes. Observe, sin embargo, que si se utilizan continuaciones de línea (\\) en lugar de comillas dobles, el preprocesador no agrega un carácter adicional por cada línea.

Mientras que una cadena entre comillas individuales no puede tener más de 2.048 bytes, se puede construir un literal de cadena de aproximadamente 65.535 bytes concatenando cadenas.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Literales de cadena de C](../c-language/c-string-literals.md)