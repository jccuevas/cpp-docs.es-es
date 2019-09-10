---
title: Pruebas de caracteres
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740098"
---
# <a name="character-testing"></a>Pruebas de caracteres

**ANSI 4.3.1** Los juegos de caracteres probados por las funciones `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint` y `isupper`.

La lista siguiente describe estas funciones tal como las implementa el compilador de Microsoft C.

|Función|Prueba|
|--------------|---------------|
|`isalnum`|Los caracteres 0 - 9, A-Z, a-z ASCII 48-57, 65-90, 97-122|
|`isalpha`|Los caracteres A-Z, a-z ASCII 65-90, 97-122|
|`iscntrl`|ASCII 0 -31, 127|
|`islower`|Los caracteres a-z ASCII 97-122|
|`isprint`|Los caracteres A-Z, a-z, 0 - 9, puntuación, espacio ASCII 32-126|
|`isupper`|Los caracteres A-Z ASCII 65-90|

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)
