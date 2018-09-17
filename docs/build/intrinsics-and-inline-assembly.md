---
title: Ensamblado intrínseco y en línea | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a87e577af339099eda56a3b9d91929a05253a43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716253"
---
# <a name="intrinsics-and-inline-assembly"></a>Ensamblado intrínseco y en línea

Una de las restricciones para el x64 compilador es no compatibles con el ensamblador alineado. Esto significa que las funciones que no se puede escribir en C o C++ tendrán que escribirse como subrutinas o funciones intrínsecas compatibles con el compilador. Algunas funciones son sensibles al rendimiento, mientras que otros no. Las funciones de sensibles al rendimiento deben implementarse como funciones intrínsecas.

En el que se describen las funciones intrínsecas compatibles con el compilador [intrínsecos del compilador](../intrinsics/compiler-intrinsics.md).

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)