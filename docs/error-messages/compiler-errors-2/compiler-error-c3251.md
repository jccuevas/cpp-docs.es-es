---
title: Error del compilador C3251
ms.date: 11/04/2016
f1_keywords:
- C3251
helpviewer_keywords:
- C3251
ms.assetid: 541c163e-5ee9-457c-a1e5-da860788b10d
ms.openlocfilehash: 1340efb50b492a7f0d9fdf159b20f5e12bf112a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554250"
---
# <a name="compiler-error-c3251"></a>Error del compilador C3251

no se puede invocar el método de clase base en una instancia de tipo de valor

El siguiente error se produce porque `GetClass` es un miembro de `Microsoft.Runtime.Object`, no de `Microsoft.Runtime.Integer4`.