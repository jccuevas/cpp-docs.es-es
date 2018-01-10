---
title: Las herramientas del vinculador LNK4014 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4014
dev_langs: C++
helpviewer_keywords: LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e0e0e87fb9c8e6006c62e07b7bb9b6435a22dd3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4014"></a>Advertencia de las herramientas del vinculador LNK4014
no se puede encontrar el objeto de miembro "objectname"  
  
 No se pudo encontrar LIB `objectname` en la biblioteca.  
  
 El **/quitar** y **/EXTRACT** opciones requieren el nombre completo del objeto miembro que se va a eliminar o copiar a un archivo. El nombre completo incluye la ruta de acceso del archivo de objeto original. Para ver los nombres completos de objetos miembro en una biblioteca, use DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) o LIB [/lista](../../build/reference/managing-a-library.md).