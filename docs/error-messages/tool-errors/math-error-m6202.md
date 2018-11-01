---
title: Error matemático M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: c216c4d01513868dd56f47c7d5ca7f8b734d1797
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538572"
---
# <a name="math-error-m6202"></a>Error matemático M6202

'function': error

Un argumento a la función especificada no era un valor de singularidad para esta función. La función no está definida para ese argumento.

Este error invoca el `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el tratamiento de determinados errores de tiempo de ejecución matemático de punto flotante.