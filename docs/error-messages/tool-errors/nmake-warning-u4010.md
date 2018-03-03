---
title: Advertencia de NMAKE U4010 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2d90e95a3417241991eb01f0ec718d75cd8558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4010"></a>Advertencia de NMAKE U4010
'target': error al generar; Se especificó/k, continuando...  
  
 Un comando en el bloque de comandos para el destino dado devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con partes de la compilación y emitir un código de salida 1 cuando finaliza la sesión NMAKE.  
  
 Si el destino dado es un dependiente de otro destino, NMAKE emite la advertencia [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) después de esta advertencia.