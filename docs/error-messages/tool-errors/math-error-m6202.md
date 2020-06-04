---
title: Error matemático M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: b8a3a4ab87a410c4cee8f7e4a1a0517c169d0364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173665"
---
# <a name="math-error-m6202"></a>Error matemático M6202

' función ': error de _SING

Un argumento de la función especificada era un valor de singularidad para esta función. La función no está definida para ese argumento.

Este error llama a la función `_matherr` con el nombre de la función, sus argumentos y el tipo de error. Puede volver a escribir la función `_matherr` para personalizar el control de determinados errores matemáticos de punto flotante en tiempo de ejecución.
