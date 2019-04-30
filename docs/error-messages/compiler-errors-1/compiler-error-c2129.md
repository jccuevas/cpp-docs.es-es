---
title: Error del compilador C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: e55107419235420d272c738e9d8ef7cf277c11c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397632"
---
# <a name="compiler-error-c2129"></a>Error del compilador C2129

función static 'function' declarada pero no definida

Se hace referencia directa a un `static` función que nunca se define.

Un `static` función debe definirse dentro del ámbito de archivo. Si la función se define en otro archivo, se debe declarar `extern`.