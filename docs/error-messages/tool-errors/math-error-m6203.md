---
title: Error matemático M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 371a6c673826c6ce71d7a0eb3b9e08d9488f53f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193698"
---
# <a name="math-error-m6203"></a>Error matemático M6203

' función ': error de _OVERFLOW

El resultado de la función especificada era demasiado grande para representarlo.

Este error llama a la función `_matherr` con el nombre de la función, sus argumentos y el tipo de error. Puede volver a escribir la función `_matherr` para personalizar el control de determinados errores matemáticos de punto flotante en tiempo de ejecución.
