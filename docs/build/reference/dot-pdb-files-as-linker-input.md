---
title: . PDB (archivos) como entrada del vinculador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5acdc01a58cf0d501be5947cddf710d1b7c6d18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="pdb-files-as-linker-input"></a>Archivos .Pdb como entrada del vinculador
Objeto (.obj) compilados con la opción/Zi contienen el nombre de una base de datos de programa (PDB). No especifique el nombre de archivo PDB del objeto al vinculador; VÍNCULO utiliza el nombre incrustado para encontrar el archivo PDB si es necesario. Esto también se aplica a los objetos depurables contenidos en una biblioteca; el archivo PDB para una biblioteca depurable debe estar disponible al vinculador junto con la biblioteca.  
  
 VÍNCULO también utiliza un archivo PDB que contiene información de depuración para el archivo .exe o .dll. La PDB del programa es un archivo de salida y un archivo de entrada, pues LINK lo actualiza cuando vuelve a generar el programa.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de entrada de vínculo](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)