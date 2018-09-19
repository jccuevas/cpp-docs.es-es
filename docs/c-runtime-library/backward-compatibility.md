---
title: Compatibilidad con versiones anteriores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3056b90f3c6f0f62158a9b6dcfe145cda9740c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092198"
---
# <a name="backward-compatibility"></a>Compatibilidad con versiones anteriores

Para la compatibilidad entre versiones del producto, la biblioteca /OLDNAMES.LIB asigna nombres anteriores a nuevos nombres. Por ejemplo, `open` se asigna a `_open`. Se debe establecer un vínculo explícito con /OLDNAMES.LIB solo cuando se compila con las siguientes combinaciones de opciones de la línea de comandos:

- `/Zl` (omitir nombres de biblioteca predeterminados del archivo objeto) y `/Ze` (valor predeterminado: usar extensiones de Microsoft)

- `/link` (control de enlazador), `/NOD` (valor no predeterminado: búsqueda de biblioteca) y `/Ze`

Para más información sobre las opciones de la línea de comandos del compilador, vea la [referencia del compilador](../build/reference/compiler-options.md).

## <a name="see-also"></a>Vea también

[Compatibilidad](../c-runtime-library/compatibility.md)