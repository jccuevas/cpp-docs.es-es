---
title: Error de las herramientas del vinculador LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 0d26ab12c5b82d52b7dcbb176d9bfa033d7ddfee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194842"
---
# <a name="linker-tools-error-lnk2004"></a>Error de las herramientas del vinculador LNK2004

desbordamiento de corrección relativo de GP en ' destino '; la sección corta ' Section ' es demasiado grande o está fuera del intervalo.

La sección era demasiado grande.

Para resolver este error, reduzca el tamaño de la sección corta, bien colocando explícitamente los datos en las secciones largas a través de #pragma sección (". sectionName", lectura, escritura, larga) y el uso de `__declspec(allocate(".sectionname"))` en definiciones y declaraciones de datos.  Por ejemplo,

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

También puede trasladar los datos agrupados lógicamente a su propia estructura que será una colección de datos de más de 8 bytes, que el compilador asignará en una sección de datos largos.  Por ejemplo,

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };
```

Este error va seguido de un error irrecuperable `LNK1165`.
