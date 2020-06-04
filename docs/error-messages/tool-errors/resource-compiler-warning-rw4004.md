---
title: Advertencia del compilador de recursos RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: ca0fb271a5ab43994ec37cc8d59c33877903f6e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182349"
---
# <a name="resource-compiler-warning-rw4004"></a>Advertencia del compilador de recursos RW4004

Carácter ASCII no equivalente a código de tecla virtual

Se usó un literal de cadena para el código de tecla virtual en un acelerador de tipo VIRTKEY.

Esta advertencia permite continuar, pero tenga en cuenta que las teclas de aceleración generadas no pueden coincidir con la cadena indicada. (los aceleradores VIRTKEY usan códigos de tecla distintos que los aceleradores ASCII).

Aunque los literales de cadena son sintácticamente válidos, solo puede asegurarse de que obtiene el acelerador que desea mediante el **VK_\* #define** valores en Windows. h.
