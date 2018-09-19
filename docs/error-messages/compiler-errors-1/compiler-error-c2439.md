---
title: Error del compilador C2439 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 419bf7be45a1383135d0231cd059837e1fe62729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058419"
---
# <a name="compiler-error-c2439"></a>Error del compilador C2439

'identifier': no se pudo inicializar el miembro

No se puede inicializar una clase, estructura o miembro de unión.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Intentando inicializar una estructura o clase base indirecta.

1. Intentando inicializar a un miembro heredado de una clase o estructura. El constructor de la clase o estructura se debe inicializar un miembro heredado.