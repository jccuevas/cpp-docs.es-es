---
title: Advertencia del compilador (nivel 1) C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 6c1b4f4ae4f60d0c4281e0bbcfc9ca2b58d81851
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408113"
---
# <a name="compiler-warning-level-1-c4445"></a>Advertencia del compilador (nivel 1) C4445

'función': un método virtual no puede ser privado en un tipo WinRT o administrado

Si una función virtual es privada, un tipo derivado no puede tener acceso a ella. Para corregir este error, cambie la accesibilidad de la función miembro virtual a protegida o pública.