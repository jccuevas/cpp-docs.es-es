---
title: Comprobación de tipos (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types
dev_langs:
- C++
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 959dd52847e6140667671b9992471155d68e9646
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="type-checking-crt"></a>Comprobación de tipos (CRT)
El compilador realiza una comprobación de tipos limitada de las funciones que pueden usar un número variable de argumentos, como sigue:  
  
|Llamada a función|Argumentos con tipos comprobados|  
|-------------------|-----------------------------|  
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|Primer argumento (cadena de formato)|  
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|Primeros dos argumentos (archivo o búfer y cadena de formato)|  
|`_snprintf_s`|Primeros tres argumentos (archivo o búfer, recuento y cadena de formato)|  
|`_open`|Primeros dos argumentos (ruta de acceso y marca `_open`)|  
|`_sopen_s`|Primeros tres argumentos (ruta de acceso, marca `_open` y modo compartido)|  
|`_execl`, `_execle`, `_execlp`, `_execlpe`|Primeros dos argumentos (ruta de acceso y primer puntero de argumento)|  
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|Primeros tres argumentos (marca de modo, ruta de acceso y primer puntero de argumento)|  
  
 El compilador realiza la misma comprobación de tipo limitada en los homólogos de caracteres anchos de estas funciones.  
  
## <a name="see-also"></a>Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)