---
title: Advertencia de NMAKE U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: aa4d2355b18a3c6cc6fc3151c7662fbbbaa665d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554263"
---
# <a name="nmake-warning-u4010"></a>Advertencia de NMAKE U4010

'target': error al generar; Se especificó/k, continuando...

Un comando en el bloque de comandos para el destino dado devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con las partes de la compilación y para emitir un código de salida 1 cuando finaliza la sesión de NMAKE.

Si el destino especificado es dependiente de otro destino, emite la advertencia de NMAKE [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) después de esta advertencia.