---
title: Las herramientas del vinculador LNK1223 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8639919c74559829367108b36d62594e2a83a91a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067998"
---
# <a name="linker-tools-error-lnk1223"></a>Error de las herramientas del vinculador LNK1223

archivo no válido o dañado: el archivo contiene contribuciones .pdata no válidas

En el caso de plataformas RISC que utilizan pdata, este error se produce si el compilador generó una sección .pdata con entradas no ordenadas.

Para corregir este problema, intente compilar sin [/GL (Whole Program Optimization)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) habilitado. Los cuerpos de función vacíos también pueden producir este error en algunos casos.