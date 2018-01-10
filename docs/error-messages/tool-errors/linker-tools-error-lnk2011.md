---
title: Las herramientas del vinculador LNK2011 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2011
dev_langs: C++
helpviewer_keywords: LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9811bdb905df61bb77ea4af6bc4ced7c4ba42106
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2011"></a>Error de las herramientas del vinculador LNK2011
objeto precompilado no vinculado; no puede ejecutar la imagen  
  
 Si se utilizan encabezados precompilados, LINK requiere que se vinculen todos los archivos objeto creados con los encabezados precompilados. Si tiene un archivo de código fuente que se usa para generar un encabezado precompilado para su uso con otros archivos de origen, ahora debe incluir el archivo objeto creado junto con el encabezado precompilado.  
  
 Por ejemplo, si compila un archivo denominado STUB.cpp para crear un encabezado precompilado para su uso con otros archivos de origen, debe vincular con STUB.obj o se producirá este error. En las siguientes líneas de comando, línea uno se utiliza para crear un encabezado precompilado, COMMON.pch, que se utiliza junto con PROG1.cpp y PROG2.cpp en las líneas dos y tres. El archivo STUB.cpp sólo contiene `#include` líneas (el mismo `#include` que en PROG1.cpp y PROG2.cpp) y sólo se utiliza para generar los encabezados precompilados. En la última línea, STUB.obj debe estar vinculado para evitar LNK2011.  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```