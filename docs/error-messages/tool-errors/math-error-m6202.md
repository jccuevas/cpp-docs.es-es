---
title: Error matemático M6202 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6202
dev_langs:
- C++
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 328336e61c299cf9b9816ddfce7212f1798eae37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058554"
---
# <a name="math-error-m6202"></a>Error matemático M6202

'function': error

Un argumento a la función especificada no era un valor de singularidad para esta función. La función no está definida para ese argumento.

Este error invoca el `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el tratamiento de determinados errores de tiempo de ejecución matemático de punto flotante.