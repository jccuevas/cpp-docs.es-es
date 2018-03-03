---
title: Error de BSCMAKE BK1503 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86f2b6d282857409cdb1e1d49e04775e9886cde4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1503"></a>Error de BSCMAKE BK1503
no se puede escribir en el archivo 'nombredearchivo' [: motivo]  
  
 BSCMAKE combina los archivos .sbr generados durante la compilación en una base de datos del explorador. Si la base de datos del explorador resultante supera los 64 MB, o si el número de archivos de entrada (.sbr) supera los 4092, se emitirá este error.  
  
 Si el problema está provocado por hay más de 4092 archivos .sbr, debe reducir el número de archivos de entrada. Desde dentro de Visual Studio, esto puede realizarse mediante [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) el proyecto completo, a continuación, volver a comprobar en forma de archivo por archivo.  
  
 Si el problema está provocado por un archivo .bsc más de 64MB, lo que reduce el número de archivos .sbr como entrada reducirá el tamaño del archivo .bsc resultante. Además, se puede reducir la cantidad de información de examen usando los /Em (excluir símbolos de expandidos de Macro), /El (excluir Variables locales) y/es (excluir archivos del sistema).  
  
## <a name="see-also"></a>Vea también  
 [Opciones de BSCMAKE](../../build/reference/bscmake-options.md)