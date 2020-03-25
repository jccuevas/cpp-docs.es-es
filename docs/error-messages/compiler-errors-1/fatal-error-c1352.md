---
title: Error irrecuperable C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: 07bd0f28e35dd2992ca537dbe744d756cc2afe80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203130"
---
# <a name="fatal-error-c1352"></a>Error irrecuperable C1352

MSIL no válido o dañado en la función 'function' del módulo 'file'

Se pasó un archivo .netmodule al compilador, pero el compilador detectó daños en el archivo.  Pida a la persona que generó el archivo .netmodule que lo investigue.

El compilador no comprueba los archivos .netmodule en busca de todos los tipos de daños.  Sin embargo, comprueba que todas las rutas de control de una función contengan una instrucción return.

Para más información, consulte [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).
