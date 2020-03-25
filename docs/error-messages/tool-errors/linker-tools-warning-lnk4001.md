---
title: Advertencia de las herramientas del vinculador LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: d9659b0cf372ff8ebc225b890fb68866872bb3d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194413"
---
# <a name="linker-tools-warning-lnk4001"></a>Advertencia de las herramientas del vinculador LNK4001

no se especificó ningún archivo objeto; bibliotecas usadas

Se pasó al vinculador uno o varios archivos. lib, pero no los archivos. obj.

Dado que el vinculador no puede tener acceso a la información de un archivo. lib al que pueda tener acceso en un archivo. obj, esta advertencia indica que tendrá que especificar explícitamente otras opciones del vinculador. Por ejemplo, puede que tenga que especificar las opciones [/Machine](../../build/reference/machine-specify-target-platform.md), [/out](../../build/reference/out-output-file-name.md)o [/entry](../../build/reference/entry-entry-point-symbol.md) .
