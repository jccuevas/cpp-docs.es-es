---
title: Tipo char
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345050"
---
# <a name="type-char"></a>Tipo char

El tipo `char` se usa para almacenar el valor entero de un miembro del juego de caracteres que se puede representar. Ese valor entero es el código ASCII correspondiente al carácter especificado.

**Específicos de Microsoft**

Los valores de carácter de tipo `unsigned char` tienen un intervalo de 0 a 0xFF hexadecimal. **signed char** tiene un intervalo de 0x80 a 0x7F. Estos intervalos se traducen a 0 a 255 decimal y -128 a +127 decimal, respectivamente. La opción del compilador /J cambia el valor predeterminado de **signed** a `unsigned`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)
