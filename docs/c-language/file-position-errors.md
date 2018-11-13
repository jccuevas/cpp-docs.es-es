---
title: Errores de posición de archivo
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: f8c1d5dfc6a599533ce8c1dcfa624d2595779f2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554614"
---
# <a name="file-position-errors"></a>Errores de posición de archivo

**ANSI 4.9.9.1, 4.9.9.4** Valor en el que establecen la macro `errno` las funciones `fgetpos` o `ftell` cuando se produce un error

Cuando `fgetpos` o `ftell` producen un error, `errno` se establece en la constante de manifiesto `EINVAL` si la posición no es válida o en `EBADF` si el número de archivo no es correcto. Las constantes se definen en ERRNO.H.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)
