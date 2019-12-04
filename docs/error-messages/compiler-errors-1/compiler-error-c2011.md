---
title: Error del compilador C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: dc13829a267deea1f412eb2d8f86057f01dc0e1c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752423"
---
# <a name="compiler-error-c2011"></a>Error del compilador C2011

'identifier': nueva definición del tipo 'type'

El identificador ya se ha definido como `type`. Busque nuevas definiciones del identificador.

También puede generarse el error C2011 si se importa varias veces un archivo de encabezado o una biblioteca de tipos al mismo archivo. Para evitar la inclusión de varias inclusiones de los tipos definidos en un archivo de encabezado, use las protecciones include o una `#pragma`una [vez](../../preprocessor/once.md) en el archivo de encabezado.

Si necesita encontrar la declaración inicial del tipo redefinido, puede usar la marca de compilador [/p](../../build/reference/p-preprocess-to-a-file.md) para generar la salida preprocesada que se pasa al compilador. Con las herramientas de búsqueda de texto, puede buscar instancias del identificador redefinido en el archivo de salida.

El ejemplo siguiente genera el error C2011 y muestra cómo corregirlo:

```cpp
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```
