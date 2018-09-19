---
title: Error del compilador C3728 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e412824bd2afdadfc21d71b73f38eb8ba5ace82d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108422"
---
# <a name="compiler-error-c3728"></a>Error del compilador C3728

'evento': evento no tiene un método raise

Los metadatos se crean con un lenguaje, como C#, que no permite que se genere desde fuera de la clase en el que se ha definido un evento, se incluyó con el [#using](../../preprocessor/hash-using-directive-cpp.md) directiva y un programa de Visual C++ mediante programación con CLR intentó genera el evento.

Para generar un evento en un programa desarrollado en un lenguaje como C#, la clase que contiene el evento debe definir también un método público que provoca el evento.