---
title: Error irrecuperable del compilador de recursos RC1120 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f28e381d4eac0bfd1f010ef3919452635a1b96
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057007"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Error irrecuperable del compilador de recursos RC1120

memoria insuficiente, necesita el número de bytes

El compilador de recursos se quedó sin almacenamiento para los elementos que almacena en su montón. Normalmente es el resultado de tener demasiados símbolos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Aumente el espacio de archivo de intercambio de Windows. Para obtener más información sobre cómo aumentar el espacio de archivo de intercambio, consulte la memoria virtual en la Ayuda de Windows.

1. Elimine los archivos de inclusión, especialmente que `#define`y función de los prototipos.

1. Divida el archivo actual en dos o más archivos y compílelos por separado.

1. Quitar otros programas o controladores que se ejecutan en el sistema, que podría estar consumiendo una cantidad significativa de memoria.