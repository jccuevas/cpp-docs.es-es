---
title: Las herramientas del vinculador LNK2027 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156310a0d21651b9fd2ee6002ace419db4996681
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301377"
---
# <a name="linker-tools-error-lnk2027"></a>Error de las herramientas del vinculador LNK2027
módulo sin resolver referencia 'module'  
  
 Un archivo que se pasa al vinculador tiene una dependencia en un módulo que se especificó ninguno con **/ASSEMBLYMODULE** ni se pasa directamente al vinculador.  
  
 Para resolver LNK2027, realice una de las siguientes acciones:  
  
-   No pase al vinculador el archivo que tiene la dependencia de módulo.  
  
-   Especifique el módulo con **/ASSEMBLYMODULE**.  
  
-   Si el módulo es un archivo .netmodule seguros, pase el módulo directamente al vinculador.  
  
 Para obtener más información, consulte [/ASSEMBLYMODULE (agregar un módulo MSIL al ensamblado)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) y [archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).