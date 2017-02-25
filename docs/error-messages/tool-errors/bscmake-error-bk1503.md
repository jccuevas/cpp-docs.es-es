---
title: "Error de BSCMAKE BK1503 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1503"
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de BSCMAKE BK1503
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede escribir en el archivo 'nombredearchivo' \[: razón\]  
  
 BSCMAKE combina los archivos .sbr generados durante la compilación en la base de datos de un explorador.  Si la base de datos del explorador resultante ocupa más de 64 MB o si el número de archivos entrantes \(.sbr\) supera los 4092, se emitirá este error.  
  
 Si el problema se debe a que hay más de 4092 archivos .sbr, hay que reducir el número de archivos entrantes.  En Visual Studio se puede realizar mediante [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) en todo el proyecto. A continuación, vuelva a comprobar cada archivo.  
  
 Si el problema está provocado por un archivo .bsc con más de 64 MB, reduzca el número de archivos .sbr entrantes para disminuir el tamaño del archivo .bsc resultante.  Además, la cantidad de información recopilada durante el examen se puede reducir usando \/Em \(excluir símbolos expandidos de macro\), \/El \(excluir variables locales\) y \/Es \(excluir archivos de sistema\).  
  
## Vea también  
 [Opciones de BSCMAKE](../../build/reference/bscmake-options.md)