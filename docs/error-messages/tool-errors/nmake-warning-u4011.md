---
title: Advertencia de NMAKE U4011 | Microsoft Docs
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
ms.openlocfilehash: a1038ee86f76789451565ab6799795c851c95a95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118341"
---
# <a name="nmake-warning-u4011"></a>Advertencia de NMAKE U4011

'target': no todos los dependientes disponibles; destino no generado

Una dependencia de destino determinado, no existe o no está actualizada, y un comando para actualizar el dependiente devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con las partes de la compilación y para emitir un código de salida 1 cuando finaliza la sesión de NMAKE.

Esta advertencia está precedida por la advertencia [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) para cada dependiente que no se pudo crear o actualizar.