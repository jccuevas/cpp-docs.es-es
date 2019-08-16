---
title: Error del compilador C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: 14969c9cdf4b00844d2001bf4817ea7ffc9bfba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361560"
---
# <a name="compiler-error-c2011"></a>Error del compilador C2011

'identifier': nueva definición del tipo 'type'

El identificador ya se ha definido como `type`. Busque nuevas definiciones del identificador.

También puede generarse el error C2011 si se importa varias veces un archivo de encabezado o una biblioteca de tipos al mismo archivo. Para evitar inclusiones múltiples de los tipos definidos en un archivo de encabezado, use restricciones de inclusión o una `#pragma` [una vez](../../preprocessor/once.md) la directiva en el archivo de encabezado.

Si necesita encontrar la declaración inicial del tipo redefinido, puede usar el [/P](../../build/reference/p-preprocess-to-a-file.md) marca de compilador para generar el resultado preprocesado que se pasó al compilador. Con las herramientas de búsqueda de texto, puede buscar instancias del identificador redefinido en el archivo de salida.

El ejemplo siguiente genera el error C2011 y muestra cómo corregirlo:

```
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```