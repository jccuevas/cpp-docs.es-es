---
title: Advertencia de NMAKE U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: f68da1893eec6325ccccfd0e2e2dd0e612f28eb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193139"
---
# <a name="nmake-warning-u4010"></a>Advertencia de NMAKE U4010

' target ': error de compilación; Se especificó/k, se continuará...

Un comando en el bloque de comandos para el destino especificado devolvió un código de salida distinto de cero. La opción/K indica a NMAKE que continúe procesando partes no relacionadas de la compilación y emita un código de salida 1 cuando finalice la sesión de NMAKE.

Si el destino especificado es, a su vez, un dependiente de otro destino, NMAKE emite una advertencia [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) después de esta advertencia.
