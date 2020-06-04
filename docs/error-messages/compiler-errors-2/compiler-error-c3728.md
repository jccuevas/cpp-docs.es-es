---
title: Error del compilador C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 8aec3ae1ff629ef7fa000182cde29e306a471315
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165880"
---
# <a name="compiler-error-c3728"></a>Error del compilador C3728

' evento ': el evento no tiene un método raise

Los metadatos creados con un lenguaje, C#como, que no permite que se genere un evento desde fuera de la clase en la que se definió, se incluyó con la directiva de [#using](../../preprocessor/hash-using-directive-cpp.md) y C++ un programa visual que utiliza la programación de CLR intentó generar el evento.

Para generar un evento en un programa desarrollado en un lenguaje como C#, la clase que contiene el evento también debe definir un método público que genere el evento.
