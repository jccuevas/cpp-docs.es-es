---
title: Advertencia de NMAKE U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 3b73e92c929b3dd5924584ab732f731d565d0430
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359779"
---
# <a name="nmake-warning-u4011"></a>Advertencia de NMAKE U4011

'target': no todos los dependientes disponibles; destino no generado

Una dependencia de destino determinado, no existe o no está actualizada, y un comando para actualizar el dependiente devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con las partes de la compilación y para emitir un código de salida 1 cuando finaliza la sesión de NMAKE.

Esta advertencia está precedida por la advertencia [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) para cada dependiente que no se pudo crear o actualizar.