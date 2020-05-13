---
title: Advertencia de las herramientas del vinculador LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: 1758fffb72e183e8a186d115b2b3f3b30c32e047
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193888"
---
# <a name="linker-tools-warning-lnk4206"></a>Advertencia de las herramientas del vinculador LNK4206

> no se encontró la información de tipo precompilado; '*filename*' no vinculado o sobrescrito; vincular objeto como si no hubiera información de depuración

El archivo de objeto de *nombre* de archivo, compilado mediante [/YC](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando Link o se sobrescribió.

Un escenario común para esta advertencia es cuando el archivo. obj que se compiló con/YC está en una biblioteca y no hay referencias de símbolos a ese. obj en el código.  En ese caso, el vinculador no usará (ni siquiera verá) el archivo. obj.  En esta situación, debe volver a compilar el código y usar [/YL](../../build/reference/yl-inject-pch-reference-for-debug-library.md) para los objetos compilados mediante [/Yu](../../build/reference/yu-use-precompiled-header-file.md).
