---
title: Advertencia del compilador (nivel 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 0c00ac552e525fd57f6f09b0be5655958cfce3cc
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075141"
---
# <a name="compiler-warning-level-1-c4727"></a>Advertencia del compilador (nivel 1) C4727

"PCH con nombre pch_file con la misma marca de tiempo encontrada en obj_file_1 y obj_file_2.  Utilizando el primer PCH.

> [!NOTE]
> En Visual Studio 2017 y versiones anteriores, el encabezado precompilado se denomina *stdafx. h* de forma predeterminada, y en Visual Studio 2019 y versiones posteriores, se llama de forma predeterminada a *PCH. h* .

C4727 se produce cuando se compilan varios compilandos con **/YC**y donde el compilador pudo marcar todos los archivos. obj con la misma marca de tiempo. pch.

Para resolverlo, compile un archivo de código fuente con **/YC/c** (crea PCH) y los demás se compilen por separado con **/Yu/c** (usa PCH) y, a continuación, vinculelos juntos.

Por lo tanto, si hizo lo siguiente y genera C4727:

::: moniker range="<=vs-2017"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycstdafx.h**

En su lugar, realizaría lo siguiente:

**CL/CLR/GL a. cpp/Ycstdafx.h/c**

**CL/CLR/GL b. cpp c. cpp/Yustdafx.h/Link a. obj**

::: moniker-end

::: moniker range=">=vs-2019"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycpch.h**

En su lugar, realizaría lo siguiente:

**CL/CLR/GL a. cpp/Ycpch.h/c**

**CL/CLR/GL b. cpp c. cpp/Yupch.h/Link a. obj**

::: moniker-end

Para obtener más información, vea

- [/Yc (Crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (Usar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md)