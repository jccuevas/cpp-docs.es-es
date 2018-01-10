---
title: Las herramientas del vinculador LNK4206 advertencia | Documentos de Microsoft
ms.date: 12/05/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4206
dev_langs: C++
helpviewer_keywords: LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd13ac59aefa074db869f0502743c7a49d23082c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4206"></a>Advertencia de las herramientas del vinculador LNK4206

> información de tipo precompilado no se encuentra; '*filename*' no vinculado o reemplazado; se vinculará el objeto sin información de depuración

El *filename* archivo de objeto, compilado mediante [/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando LINK o se sobrescribió.

Un escenario común para esta advertencia es cuando el archivo .obj que se compiló con/Yc está en una biblioteca, y donde no hay ningún símbolo hace referencia a dicho archivo .obj desde el código.  En ese caso, el vinculador no use (ni incluso ver) del archivo .obj.  En esta situación, debe volver a compilar el código y usar [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) para los objetos compilados mediante [/Yu](../../build/reference/yu-use-precompiled-header-file.md).