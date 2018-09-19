---
title: Compilador advertencia (nivel 4) C4057 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b10ce6b67fd24b4b8db01177af0225deab9dba4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088012"
---
# <a name="compiler-warning-level-4-c4057"></a>Advertencia del compilador (nivel 4) C4057

'operador': direccionamiento indirecto de 'identificador1' a tipos base ligeramente distintos de 'identificador2'.

Dos expresiones de puntero hacen referencia a diferentes tipos base. Las expresiones se usan sin conversión.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Combinación de tipos con signo y sin signo.

1. Combinación de tipos **short** y **long** .