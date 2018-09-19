---
title: Las herramientas del vinculador LNK1140 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f850360bc749a41e548cebae9f58f9fc7d3d420
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044709"
---
# <a name="linker-tools-error-lnk1140"></a>Error de las herramientas del vinculador LNK1140

demasiados módulos para la base de datos de programa; vincule con/PDB: NONE

El proyecto contiene más de 4096 módulos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Vuelva a vincular con [/PDB: NONE](../../build/reference/pdb-use-program-database.md).

1. Algunos módulos se compile sin información de depuración.

1. Reduzca el número de módulos.