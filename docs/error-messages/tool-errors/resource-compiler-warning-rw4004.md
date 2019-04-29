---
title: Advertencia del compilador de recursos RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: bafd1084a665fc656fe184064a48e5fffc61c957
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346085"
---
# <a name="resource-compiler-warning-rw4004"></a>Advertencia del compilador de recursos RW4004

Carácter ASCII no equivalente a código de tecla virtual

Se usó un literal de cadena para el código de tecla virtual en un acelerador de tipo VIRTKEY.

Esta advertencia permite continuar, pero tenga en cuenta que las teclas de aceleración generadas no pueden coincidir con la cadena indicada. (los aceleradores VIRTKEY usan códigos de tecla distintos que los aceleradores ASCII).

Mientras los literales de cadena sean válidos sintácticamente, sólo se puede asegurar que se consigue el acelerador deseado mediante el **VK_\* #define** valores en WINDOWS.h.