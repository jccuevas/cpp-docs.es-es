---
title: Advertencia de NMAKE U4010 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc8c99bb4a9b5daf7f630771d0f240479aaf5f3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316548"
---
# <a name="nmake-warning-u4010"></a>Advertencia de NMAKE U4010
'target': error al generar; Se especificó/k, continuando...  
  
 Un comando en el bloque de comandos para el destino dado devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con partes de la compilación y emitir un código de salida 1 cuando finaliza la sesión NMAKE.  
  
 Si el destino dado es un dependiente de otro destino, NMAKE emite la advertencia [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) después de esta advertencia.