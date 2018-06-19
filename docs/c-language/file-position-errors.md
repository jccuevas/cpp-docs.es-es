---
title: Errores de posición de archivo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71c059939891680b638e8644f7902d54452f5332
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383226"
---
# <a name="file-position-errors"></a>Errores de posición de archivo
**ANSI 4.9.9.1, 4.9.9.4** Valor en el que establecen la macro `errno` las funciones `fgetpos` o `ftell` cuando se produce un error  
  
 Cuando `fgetpos` o `ftell` producen un error, `errno` se establece en la constante de manifiesto `EINVAL` si la posición no es válida o en `EBADF` si el número de archivo no es correcto. Las constantes se definen en ERRNO.H.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)
