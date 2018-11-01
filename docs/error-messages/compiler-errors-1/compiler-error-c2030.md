---
title: Error del compilador C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: 217f97d205e1da075277b8b0bc22ff3baab13482
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602181"
---
# <a name="compiler-error-c2030"></a>Error del compilador C2030

un destructor con accesibilidad 'protected private' no puede ser miembro de una clase declarada 'sealed'

Una clase de Windows Runtime declarada como `sealed` no puede tener un destructor privado protegido. En tipos sealed solo se permiten destructores no virtuales privados y virtuales públicos. Para obtener más información, consulte [clases y structs Ref](../../cppcx/ref-classes-and-structs-c-cx.md).

Para corregir este error, cambie la accesibilidad del destructor.