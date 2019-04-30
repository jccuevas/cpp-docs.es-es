---
title: Error del compilador C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328112"
---
# <a name="compiler-error-c3728"></a>Error del compilador C3728

'evento': evento no tiene un método raise

Los metadatos se crean con un lenguaje, como C#, que no permite que se genere desde fuera de la clase en el que se ha definido un evento, se incluyó con el [#using](../../preprocessor/hash-using-directive-cpp.md) directiva y un programa de Visual C++ mediante programación con CLR intentó genera el evento.

Para generar un evento en un programa desarrollado en un lenguaje como C#, la clase que contiene el evento debe definir también un método público que provoca el evento.