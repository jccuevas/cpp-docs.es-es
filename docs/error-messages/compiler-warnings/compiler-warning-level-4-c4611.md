---
title: Advertencia del compilador (nivel 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 7de4cdf0eacb1b9848a4350f1d223da1fd47d1fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198307"
---
# <a name="compiler-warning-level-4-c4611"></a>Advertencia del compilador (nivel 4) C4611

la interacción entre ' función ' C++ y la destrucción de objetos no es portátil

En algunas plataformas, las funciones que incluyen **catch** pueden no C++ admitir la semántica de objetos de destrucción cuando están fuera del ámbito.

Para evitar un comportamiento inesperado, evite usar **catch** en funciones que tengan constructores y destructores.

Esta advertencia solo se emite una vez; vea [pragma warning](../../preprocessor/warning.md).
