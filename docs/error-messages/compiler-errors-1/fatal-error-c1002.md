---
title: Error irrecuperable C1002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f08255484b11f9f5d87fb67ac8ac7b401d4f6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044150"
---
# <a name="fatal-error-c1002"></a>Error irrecuperable C1002

el compilador no tiene espacio en el montón en el paso 2

El compilador se quedó sin espacio de memoria dinámica durante su segunda pasada, probablemente debido a un programa con demasiados símbolos o expresiones complejas.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Dividir el archivo de código fuente en varios archivos más pequeños.

1. Divida las expresiones en subexpresiones más pequeñas.

1. Quitar otros programas o controladores que consuman memoria.