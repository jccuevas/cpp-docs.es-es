---
title: Error grave de NMAKE U1035 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0383bf4742d637d669070efa5370ebda0c7ab159
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019866"
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