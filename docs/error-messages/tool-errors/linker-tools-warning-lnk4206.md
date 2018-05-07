---
title: Las herramientas del vinculador LNK4206 advertencia | Documentos de Microsoft
ms.date: 12/05/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4206
dev_langs:
- C++
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0cb74776f307affb0455d972e27e594e6d06294
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4206"></a>Advertencia de las herramientas del vinculador LNK4206

> información de tipo precompilado no se encuentra; '*filename*' no vinculado o reemplazado; se vinculará el objeto sin información de depuración

El *filename* archivo de objeto, compilado mediante [/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando LINK o se sobrescribió.

Un escenario común para esta advertencia es cuando el archivo .obj que se compiló con/Yc está en una biblioteca, y donde no hay ningún símbolo hace referencia a dicho archivo .obj desde el código.  En ese caso, el vinculador no use (ni incluso ver) del archivo .obj.  En esta situación, debe volver a compilar el código y usar [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) para los objetos compilados mediante [/Yu](../../build/reference/yu-use-precompiled-header-file.md).