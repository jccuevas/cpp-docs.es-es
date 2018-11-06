---
title: Error grave de NMAKE U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 9c4055bb99243f7d20c1da90aef7b916c46c2749
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589496"
---
# <a name="nmake-fatal-error-u1035"></a>Error grave de NMAKE U1035

error de sintaxis: se esperaba ':' o '=' separador

Dos puntos (**:**) o un signo igual (**=**) se esperaba.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Un destino no iba seguido de dos puntos.

1. Dos puntos y sin espacio (por ejemplo, a:) habían seguido de un destino de letra única. NMAKE lo interpreta como una especificación de unidad.

1. Dos puntos no seguían una regla de inferencia.

1. Una definición de macro no iba seguida de un signo igual.

1. Un carácter seguido de una barra diagonal inversa (**\\**) que se usó para continuar un comando en una nueva línea.

1. Una cadena que no iba seguido de cualquier regla de sintaxis NMAKE aparecido.

1. El archivo MAKE se da formato a un procesador de textos.