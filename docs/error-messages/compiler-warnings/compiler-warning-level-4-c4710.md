---
title: Compilador advertencia (nivel 4) C4710 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f6de17f7005db3834bfcfc93aff03f12f0293ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046100"
---
# <a name="compiler-warning-level-4-c4710"></a>Advertencia del compilador (nivel 4) C4710

'function': función no está entre línea

La función especificada se ha seleccionado para la expansión en línea, pero el compilador no llevó a cabo la inserción.

La inserción se realiza a discreción del compilador. El **inline** palabra clave, como el **registrar** palabra clave, se utiliza como una sugerencia para el compilador. El compilador usa la heurística para determinar si debe insertar una función concreta para acelerar el código al compilar para acelerar el proceso, o si debe insertar una función concreta para reducir el código al compilar para el espacio. El compilador incluirá solo funciones muy pequeñas al compilar para el espacio.

En algunos casos, el compilador no insertará una determinada función por motivos mecánicos. Consulte [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) para obtener una lista de motivos por los que el compilador no alinea una función.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.