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
ms.openlocfilehash: 8def11317548bfd6e70badab4563891c1b6f864d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031927"
---
# <a name="file-position-errors"></a>Errores de posición de archivo

**ANSI 4.9.9.1, 4.9.9.4** Valor en el que establecen la macro `errno` las funciones `fgetpos` o `ftell` cuando se produce un error

Cuando `fgetpos` o `ftell` producen un error, `errno` se establece en la constante de manifiesto `EINVAL` si la posición no es válida o en `EBADF` si el número de archivo no es correcto. Las constantes se definen en ERRNO.H.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)
