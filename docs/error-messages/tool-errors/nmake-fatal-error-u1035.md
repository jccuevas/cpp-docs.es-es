---
title: Error grave de NMAKE U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 9c4055bb99243f7d20c1da90aef7b916c46c2749
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324342"
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