---
title: Error del compilador C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: 3b688012009a87c1e3d0db05e47133893daeaf34
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451069"
---
# <a name="compiler-error-c3398"></a>Error del compilador C3398

'operador': no se puede convertir de 'signatura_de_función' a 'puntero_a_función'. La expresión de origen debe ser un símbolo de función

Si no se especifica la convención de llamada [__clrcall](../../cpp/clrcall.md) cuando se compila con **/clr**, el compilador genera dos puntos de entrada (direcciones) para cada función, un punto de entrada nativo y un punto de entrada administrado.

De forma predeterminada, el compilador devuelve el punto de entrada nativo, pero hay algunos casos en los que se desea el punto de entrada administrado (por ejemplo, al asignar la dirección a un puntero a función `__clrcall` ). Para que el compilador elija correctamente el punto de entrada administrado en una asignación, el lado derecho debe ser un símbolo de función.