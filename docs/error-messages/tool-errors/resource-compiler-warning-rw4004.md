---
title: Advertencia del compilador de recursos RW4004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33305f1f86c0cc1722e4a235ec27927f6e70675f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095994"
---
# <a name="resource-compiler-warning-rw4004"></a>Advertencia del compilador de recursos RW4004

Carácter ASCII no equivalente a código de tecla virtual

Se usó un literal de cadena para el código de tecla virtual en un acelerador de tipo VIRTKEY.

Esta advertencia permite continuar, pero tenga en cuenta que las teclas de aceleración generadas no pueden coincidir con la cadena indicada. (los aceleradores VIRTKEY usan códigos de tecla distintos que los aceleradores ASCII).

Mientras los literales de cadena sean válidos sintácticamente, sólo se puede asegurar que se consigue el acelerador deseado mediante el **VK_\* #define** valores en WINDOWS.h.