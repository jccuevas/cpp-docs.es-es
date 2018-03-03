---
title: Advertencia de NMAKE U4011 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ae15a3912fe3172e9dec98e1a90a3a262c47117
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4011"></a>Advertencia de NMAKE U4011
'target': no todos los dependientes disponibles; no se ha creado el destino  
  
 Una dependencia de destino determinado, no existe o no está actualizada, y un comando para actualizar el dependiente devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con partes de la compilación y emitir un código de salida 1 cuando finaliza la sesión NMAKE.  
  
 Esta advertencia es precedida de la advertencia [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) para cada dependiente que no se pudo crear o actualizar.