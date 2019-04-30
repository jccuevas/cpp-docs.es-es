---
title: Error del compilador C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406852"
---
# <a name="compiler-error-c2856"></a>Error del compilador C2856

\#pragma hdrstop no puede estar dentro de un bloque #if

El `hdrstop` pragma no se puede colocar dentro del cuerpo de un bloque de compilación condicional.

Mover el `#pragma hdrstop` instrucción a un área que no está contenido en un `#if/#endif` bloque.