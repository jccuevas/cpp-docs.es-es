---
title: Error de las herramientas del vinculador LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 845c796ee9611e921e2fd1707b9bb956ab62a5ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195271"
---
# <a name="linker-tools-error-lnk1140"></a>Error de las herramientas del vinculador LNK1140

demasiados módulos para la base de datos de programa; vincular con/PDB: NONE

El proyecto contiene más de 4096 módulos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Volver a vincular con [/PDB: None](../../build/reference/pdb-use-program-database.md).

1. Compilar algunos módulos sin información de depuración.

1. Reduzca el número de módulos.
