---
title: Las herramientas del vinculador LNK1245 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef7bace5cec937399d7a2ed440e21b9b751f4141
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041797"
---
# <a name="linker-tools-error-lnk1245"></a>Error de las herramientas del vinculador LNK1245

subsistema 'subsistema' especificado; /SUBSYSTEM debe ser WINDOWS, WINDOWSCE o CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) se utilizó para compilar el objeto y una de las siguientes condiciones era true:

- Se ha definido un punto de entrada personalizado ([/Entry](../../build/reference/entry-entry-point-symbol.md)), de modo que el vinculador no puede inferir un subsistema.

- Se pasó un valor a la [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opción del vinculador que no es válido para los objetos / CLR.

En ambos casos, la resolución es especificar un valor válido para la opción de vinculador/SUBSYSTEM.