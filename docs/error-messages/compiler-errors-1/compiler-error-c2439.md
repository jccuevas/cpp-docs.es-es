---
title: Error del compilador C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 99f3644869f6c5395684643f0e7802f3a01baa62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205366"
---
# <a name="compiler-error-c2439"></a>Error del compilador C2439

' Identifier ': no se pudo inicializar el miembro

No se puede inicializar un miembro de clase, estructura o Unión.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Intentando inicializar una clase o estructura base indirecta.

1. Intento de inicializar un miembro heredado de una clase o estructura. El constructor de la clase o estructura debe inicializar un miembro heredado.
