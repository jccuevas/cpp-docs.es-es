---
title: Error irrecuperable C1352 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1352
dev_langs:
- C++
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 524b0bf5d25953c5c38cbe0e23dc5c7d9f3cb7be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226824"
---
# <a name="fatal-error-c1352"></a>Error irrecuperable C1352
MSIL no válido o dañado en la función 'function' del módulo 'file'  
  
 Se pasó un archivo .netmodule al compilador, pero el compilador detectó daños en el archivo.  Pida a la persona que generó el archivo .netmodule que lo investigue.  
  
 El compilador no comprueba los archivos .netmodule en busca de todos los tipos de daños.  Sin embargo, comprueba que todas las rutas de control de una función contengan una instrucción return.  
  
 Para más información, consulte [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).