---
title: Las herramientas del vinculador LNK4014 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb86efbdc70342861a87a233ab687f7564cb48b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4014"></a>Advertencia de las herramientas del vinculador LNK4014
no se puede encontrar el objeto de miembro "objectname"  
  
 No se pudo encontrar LIB `objectname` en la biblioteca.  
  
 El **/quitar** y **/EXTRACT** opciones requieren el nombre completo del objeto miembro que se va a eliminar o copiar a un archivo. El nombre completo incluye la ruta de acceso del archivo de objeto original. Para ver los nombres completos de objetos miembro en una biblioteca, use DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) o LIB [/lista](../../build/reference/managing-a-library.md).