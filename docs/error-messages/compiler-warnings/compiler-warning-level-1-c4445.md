---
title: Advertencia del compilador (nivel 1) C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 2956758a6bdd074d7fc902c6ebac60af19e34b54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186769"
---
# <a name="compiler-warning-level-1-c4445"></a>Advertencia del compilador (nivel 1) C4445

'función': un método virtual no puede ser privado en un tipo WinRT o administrado

Si una función virtual es privada, un tipo derivado no puede tener acceso a ella. Para corregir este error, cambie la accesibilidad de la función miembro virtual a protegida o pública.
