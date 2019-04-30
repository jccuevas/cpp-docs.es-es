---
title: Advertencia de las herramientas del vinculador LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: dc81df89609f59834c8a3271dd64f3b99b281f90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395084"
---
# <a name="linker-tools-warning-lnk4206"></a>Advertencia de las herramientas del vinculador LNK4206

> información de tipo precompilado que no se encuentra; '*filename*' no vinculado o reemplazado; se vinculará el objeto sin información de depuración

El *filename* archivo objeto compilado con [/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando de vínculo o se ha sobrescrito.

Un escenario común para esta advertencia es cuando el archivo .obj que se compiló con/Yc está en una biblioteca, y donde no hay ningún símbolo hace referencia a dicho archivo .obj desde el código.  En ese caso, el vinculador no use (ni incluso ver) del archivo .obj.  En esta situación, debe volver a compilar el código y usar [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) para los objetos compilados mediante [/Yu](../../build/reference/yu-use-precompiled-header-file.md).