---
title: Caracteres anchos
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 868acf0abd26a1f4b5533bb997fb9ea09a27954b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151967"
---
# <a name="wide-characters"></a>Caracteres anchos

**ANSI 3.1.3.4** Valor de una constante de caracteres enteros que contiene más de un carácter o una constante de caracteres anchos que contiene más de un carácter multibyte

La constante de caracteres normales "ab" tiene el valor entero (int)0x6162. Cuando hay más de un byte, los bytes de lectura anteriores se desplazan a la izquierda según el valor de **CHAR_BIT** y el byte siguiente se compara mediante el operador OR bit a bit con los bits inferiores de **CHAR_BIT**. El número de bytes de la constante de caracteres multibyte no puede superar sizeof(int), que es 4 para el código de 32 bits de destino.

La constante de caracteres multibyte se lee como se indica arriba y se convierte en una constante de caracteres anchos mediante la función en tiempo de ejecución `mbtowc`. Si el resultado no es una constante de caracteres anchos válida, se produce un error. En cualquier caso, el número de bytes examinados por la función `mbtowc` se limita al valor de `MB_CUR_MAX`.

## <a name="see-also"></a>Vea también

[Caracteres](../c-language/characters.md)
