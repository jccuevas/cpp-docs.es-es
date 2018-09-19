---
title: Error de BSCMAKE BK1509 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1509
dev_langs:
- C++
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 091fab63737c7ee1b3b85753a354bb7214cfa411
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025248"
---
# <a name="bscmake-error-bk1509"></a>Error de BSCMAKE BK1509

espacio de montón insuficiente

BSCMAKE se quedó sin memoria, incluida la memoria virtual.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Libere espacio en disco.

1. Aumentar el tamaño del archivo de intercambio.

1. Aumentar el tamaño del archivo de intercambio de Windows.

1. Reduzca la memoria que requiere BSCMAKE mediante/EI o/es para eliminar algunos archivos de entrada o /Em para eliminar los cuerpos de macro.