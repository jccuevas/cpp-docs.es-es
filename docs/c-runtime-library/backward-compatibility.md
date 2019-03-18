---
title: Compatibilidad con versiones anteriores
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: f672f0601a9d20a726f90963265d08ec212dedce
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744477"
---
# <a name="backward-compatibility"></a>Compatibilidad con versiones anteriores

Para la compatibilidad entre versiones del producto, la biblioteca /OLDNAMES.LIB asigna nombres anteriores a nuevos nombres. Por ejemplo, `open` se asigna a `_open`. Se debe establecer un vínculo explícito con /OLDNAMES.LIB solo cuando se compila con las siguientes combinaciones de opciones de la línea de comandos:

- `/Zl` (omitir nombres de biblioteca predeterminados del archivo objeto) y `/Ze` (valor predeterminado: usar extensiones de Microsoft)

- `/link` (control de enlazador), `/NOD` (valor no predeterminado: búsqueda de biblioteca) y `/Ze`

Para más información sobre las opciones de la línea de comandos del compilador, vea la [referencia del compilador](../build/reference/compiler-options.md).

## <a name="see-also"></a>Vea también

[Compatibilidad](../c-runtime-library/compatibility.md)
