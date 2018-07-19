---
title: Pruebas de caracteres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdf65de941486cb8256ba8e30a3f186d3e3702d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381699"
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