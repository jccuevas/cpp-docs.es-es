---
title: Advertencia del compilador (nivel 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 45d2db56a7b0fc871de60743954012faf0f5c366
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185391"
---
# <a name="compiler-warning-level-4-c4057"></a>Advertencia del compilador (nivel 4) C4057

'operador': direccionamiento indirecto de 'identificador1' a tipos base ligeramente distintos de 'identificador2'.

Dos expresiones de puntero hacen referencia a diferentes tipos base. Las expresiones se usan sin conversión.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Combinación de tipos con signo y sin signo.

1. Combinación de tipos **short** y **long** .
