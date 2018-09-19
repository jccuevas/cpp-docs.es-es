---
title: . Los archivos PDB como entrada del vinculador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b728903d2a270efc6b3eb736e45540651dae8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706191"
---
# <a name="pdb-files-as-linker-input"></a>Archivos .Pdb como entrada del vinculador

Objeto (.obj) compilados con la opción/Zi contienen el nombre de una base de datos de programa (PDB). No se especifica el nombre del objeto PDB archivo al vinculador; VÍNCULO utiliza el nombre incrustado para encontrar el archivo PDB, si es necesario. Esto también se aplica a objetos depurables contenidos en una biblioteca; el archivo PDB para una biblioteca depurable debe estar disponible para el vinculador junto con la biblioteca.

VÍNCULO también utiliza un archivo PDB que contiene información de depuración para el archivo .exe o .dll. PDB del programa es un archivo de salida y un archivo de entrada, porque el vínculo actualiza el archivo PDB cuando vuelve a compilar el programa.

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](../../build/reference/link-input-files.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)