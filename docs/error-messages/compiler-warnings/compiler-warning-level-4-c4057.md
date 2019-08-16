---
title: Advertencia del compilador (nivel 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 234223ee7b6a031dd9e2c0fc88ccbbdba05beb3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401441"
---
# <a name="compiler-warning-level-4-c4057"></a>Advertencia del compilador (nivel 4) C4057

'operador': direccionamiento indirecto de 'identificador1' a tipos base ligeramente distintos de 'identificador2'.

Dos expresiones de puntero hacen referencia a diferentes tipos base. Las expresiones se usan sin conversión.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Combinación de tipos con signo y sin signo.

1. Combinación de tipos **short** y **long** .