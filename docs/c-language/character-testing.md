---
title: Pruebas de caracteres
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147196"
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
