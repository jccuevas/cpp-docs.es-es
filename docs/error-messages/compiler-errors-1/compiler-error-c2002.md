---
title: Error del compilador C2002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87a7fe1513c695344676624ae1968060097c885
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116924"
---
# <a name="compiler-error-c2002"></a>Error del compilador C2002

constante de caracteres anchos no válida

La constante de caracteres multibyte no es válida.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. La constante de caracteres anchos contiene más bytes de lo esperado.

1. No se incluye el encabezado estándar STDDEF.h.

1. Caracteres anchos no se pueden concatenar con literales de cadena normal.

1. Una constante de caracteres anchos debe ir precedida por el carácter 'L':

    ```
    L'mbconst'
    ```

1. En Microsoft C++, los argumentos de texto de una directiva de preprocesador deben ser ASCII. Por ejemplo, la directiva, `#pragma message(L"string")`, no es válido.