---
title: Error irrecuperable C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 6ed70a81c4ae2028d09b694f325f83454e99a587
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203104"
---
# <a name="fatal-error-c1382"></a>Error irrecuperable C1382

el archivo PCH ' file ' se ha recompilado desde que se generó ' obj '. Recompile este objeto

Al usar [/LTCG](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un archivo. pch que es más reciente que un cil. obj que apunta a él. La información del archivo CIL. obj no está actualizada. Vuelva a generar el objeto.

C1382 también se puede producir si se compila con **/YC**, pero también se pasan varios archivos de código fuente al compilador.  Para resolverlo, no use **/YC** al pasar varios archivos de código fuente al compilador.  Para obtener más información, vea [/YC (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md).
