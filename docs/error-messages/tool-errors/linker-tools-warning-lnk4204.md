---
title: "Advertencia de las herramientas del vinculador LNK4204 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4204"
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Advertencia de las herramientas del vinculador LNK4204
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

falta información de depuración de 'nombredearchivo' para hacer referencia al módulo; se vinculará el objeto sin tener en cuenta información de depuración  
  
 El archivo .pdb tiene una firma errónea.  El vinculador continuará vinculando el objeto sin información de depuración.  Puede resultar conveniente volver a compilar el archivo objeto con la opción [Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 La advertencia LNK4204 puede producirse si algunos de los objetos de la biblioteca hacen referencia a un archivo que ya no existe.  Esto puede ocurrir, por ejemplo, al recompilar la solución; podría eliminarse un archivo objeto y no recompilarse debido a un error de compilación.  En este caso, tendrá que compilar con **\/Z7** o **\/Fd** para actualizar los objetos de modo que hagan referencia a un único archivo por biblioteca \(no se trata del nombre de archivo .pdb predeterminado\).  Para obtener más información, vea [\/Fd \(Nombre del archivo de base de datos del programa\)](../../build/reference/fd-program-database-file-name.md).  Asegúrese de que el archivo .pdb se guarde con la biblioteca cada vez que se actualice en el sistema de control de código fuente.