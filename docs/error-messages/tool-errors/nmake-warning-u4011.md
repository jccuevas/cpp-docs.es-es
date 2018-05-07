---
title: Advertencia de NMAKE U4011 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9c0f90c507eebe212a9c3cbfb2f2d21cded43d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-warning-u4011"></a>Advertencia de NMAKE U4011
'target': no todos los dependientes disponibles; no se ha creado el destino  
  
 Una dependencia de destino determinado, no existe o no está actualizada, y un comando para actualizar el dependiente devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con partes de la compilación y emitir un código de salida 1 cuando finaliza la sesión NMAKE.  
  
 Esta advertencia es precedida de la advertencia [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) para cada dependiente que no se pudo crear o actualizar.