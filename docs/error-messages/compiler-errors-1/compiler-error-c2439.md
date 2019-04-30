---
title: Error del compilador C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: f71112d3f37f3e4d1a4f41bade95726d7aa0a0bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311740"
---
# <a name="compiler-error-c2439"></a>Error del compilador C2439

'identifier': no se pudo inicializar el miembro

No se puede inicializar una clase, estructura o miembro de unión.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Intentando inicializar una estructura o clase base indirecta.

1. Intentando inicializar a un miembro heredado de una clase o estructura. El constructor de la clase o estructura se debe inicializar un miembro heredado.