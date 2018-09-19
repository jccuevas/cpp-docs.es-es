---
title: Error irrecuperable C1382 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a5a6ce312c5ef886ef25e8de46e6d3376eded2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030662"
---
# <a name="fatal-error-c1382"></a>Error irrecuperable C1382

el archivo PCH 'archivo' se ha recompilado desde que se generó 'obj'. Recompile este objeto

Cuando se usa [/LTCG](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un archivo .pch más reciente que un archivo .obj CIL que hace referencia a ella. La información en el archivo obj CIL es obsoleta. Vuelva a generar el objeto.

C1382 también puede producirse si se compila con **/Yc**, pero también pasar varios orígenes de archivos de código para el compilador.  Para resolver, no use **/Yc** al pasar varios orígenes de archivos de código para el compilador.  Para obtener más información, consulte [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md).