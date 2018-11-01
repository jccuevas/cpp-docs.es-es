---
title: Error del compilador C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: e55107419235420d272c738e9d8ef7cf277c11c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593467"
---
# <a name="compiler-error-c2129"></a>Error del compilador C2129

función static 'function' declarada pero no definida

Se hace referencia directa a un `static` función que nunca se define.

Un `static` función debe definirse dentro del ámbito de archivo. Si la función se define en otro archivo, se debe declarar `extern`.