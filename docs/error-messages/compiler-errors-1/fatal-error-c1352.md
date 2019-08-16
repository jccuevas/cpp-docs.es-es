---
title: Error irrecuperable C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329730"
---
# <a name="fatal-error-c1352"></a>Error irrecuperable C1352

MSIL no válido o dañado en la función 'function' del módulo 'file'

Se pasó un archivo .netmodule al compilador, pero el compilador detectó daños en el archivo.  Pida a la persona que generó el archivo .netmodule que lo investigue.

El compilador no comprueba los archivos .netmodule en busca de todos los tipos de daños.  Sin embargo, comprueba que todas las rutas de control de una función contengan una instrucción return.

Para más información, consulte [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).