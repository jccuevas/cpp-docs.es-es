---
title: ADVERTENCIA del compilador (nivel 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: 214ccae5d9835bc4a3b66bbbe1cd5ded4bc651cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164149"
---
# <a name="compiler-warning-level-1-c4049"></a>ADVERTENCIA del compilador (nivel 1) C4049

límite del compilador: emisión de número de línea de terminación

El archivo contiene más de 16.777.215 (2<sup>24</sup>-1) líneas de código fuente. El compilador detiene la numeración en 16.777.215.

Para el código después de la línea 16.777.215:

- La imagen no contendrá ninguna información de depuración para los números de línea.

- Es posible que se notifiquen algunos diagnósticos con números de línea incorrectos.

- las listas de. ASM (/FAs) pueden tener números de línea incorrectos.
