---
title: Advertencia de NMAKE U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 6b1701ffc83f849d2482bd14b25d65c04c496899
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193152"
---
# <a name="nmake-warning-u4011"></a>Advertencia de NMAKE U4011

' target ': no todos los dependientes disponibles; destino no compilado

Un dependiente del destino especificado no existe o no está actualizado, y un comando para actualizar el dependiente devuelve un código de salida distinto de cero. La opción/K indica a NMAKE que continúe procesando partes no relacionadas de la compilación y emita un código de salida 1 cuando finalice la sesión de NMAKE.

Esta advertencia va precedida de la advertencia [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) para cada dependiente que no se pudo crear o actualizar.
