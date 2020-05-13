---
title: Error grave de NMAKE U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 3eda424574dfa48901cf4dc6aea3b28beb739dc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193724"
---
# <a name="nmake-fatal-error-u1035"></a>Error grave de NMAKE U1035

error de sintaxis: se esperaba el separador ': ' o ' = '

Se esperaba un signo de dos puntos ( **:** ) o un signo igual ( **=** ).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Un signo de dos puntos no siguió un destino.

1. Dos puntos y sin espacio (por ejemplo,:) seguido de un destino de una sola letra. NMAKE lo interpreta como una especificación de unidad.

1. Un signo de dos puntos no siguió una regla de inferencia.

1. Una definición de macro no iba seguida de un signo igual.

1. Carácter seguido de una barra diagonal inversa ( **\\** ) que se usó para continuar un comando en una nueva línea.

1. Aparece una cadena que no siguió ninguna regla de sintaxis de NMAKE.

1. Un procesador de textos dio formato al archivo make.
