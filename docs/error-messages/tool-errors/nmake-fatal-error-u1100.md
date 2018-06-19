---
title: Error grave de NMAKE U1100 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d4ed57c980813c8539fbffed0e41a35048c0571
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319623"
---
# <a name="nmake-fatal-error-u1100"></a>Error grave de NMAKE U1100
macro 'nombredemacro' no es válida en el contexto de la regla por lotes 'regla'  
  
 NMAKE genera este error cuando el bloque de comandos de una regla de modo por lotes directa o indirectamente hace referencia a una macro de archivo especial que no es $<.  
  
 $< solo se permite la macro para las reglas de modo por lotes.