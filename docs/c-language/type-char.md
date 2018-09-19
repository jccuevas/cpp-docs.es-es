---
title: Tipo char | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec964d9b81ee93f888bbd4152f06f6bdf51b6d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053835"
---
# <a name="type-char"></a>Tipo char

El tipo `char` se usa para almacenar el valor entero de un miembro del juego de caracteres que se puede representar. Ese valor entero es el código ASCII correspondiente al carácter especificado.

**Específicos de Microsoft**

Los valores de carácter de tipo `unsigned char` tienen un intervalo de 0 a 0xFF hexadecimal. **signed char** tiene un intervalo de 0x80 a 0x7F. Estos intervalos se traducen a 0 a 255 decimal y -128 a +127 decimal, respectivamente. La opción del compilador /J cambia el valor predeterminado de **signed** a `unsigned`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)