---
title: Error irrecuperable C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 2b7f6fd878f0d0ba6cde19a3a316a01c390e954a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228569"
---
# <a name="fatal-error-c1382"></a>Error irrecuperable C1382

el archivo PCH 'archivo' se ha recompilado desde que se generó 'obj'. Recompile este objeto

Cuando se usa [/LTCG](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un archivo .pch más reciente que un archivo .obj CIL que hace referencia a ella. La información en el archivo obj CIL es obsoleta. Vuelva a generar el objeto.

C1382 también puede producirse si se compila con **/Yc**, pero también pasar varios orígenes de archivos de código para el compilador.  Para resolver, no use **/Yc** al pasar varios orígenes de archivos de código para el compilador.  Para obtener más información, consulte [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md).