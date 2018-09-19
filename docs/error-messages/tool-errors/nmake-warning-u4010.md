---
title: Advertencia de NMAKE U4010 | Microsoft Docs
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
ms.openlocfilehash: a640245db460f4cd8cd658c097955a69a59d1fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117509"
---
# <a name="nmake-warning-u4010"></a>Advertencia de NMAKE U4010

'target': error al generar; Se especificó/k, continuando...

Un comando en el bloque de comandos para el destino dado devolvió un código de salida distinto de cero. La opción /K indicó a NMAKE para continuar el procesamiento relacionado con las partes de la compilación y para emitir un código de salida 1 cuando finaliza la sesión de NMAKE.

Si el destino especificado es dependiente de otro destino, emite la advertencia de NMAKE [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) después de esta advertencia.