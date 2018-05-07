---
title: Error de línea de comandos D8027 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc93edb939001a1e1bed5d3f7a4113e8483e81dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-error-d8027"></a>Error de la línea de comandos D8027
no se puede ejecutar 'componente'  
  
 El compilador no pudo ejecutar el componente del compilador dado o vinculador.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  No hay suficiente memoria para cargar el componente. Si NMAKE invoca el compilador, ejecute el compilador fuera del archivo MAKE.  
  
2.  El sistema operativo actual no pudo ejecutar el componente. Asegúrese de que los puntos de ruta de acceso a los archivos ejecutables adecuados para su sistema operativo.  
  
3.  El componente está dañado. Volver a copiar el componente de los discos de distribución mediante el programa de instalación.  
  
4.  Se especificó una opción incorrectamente. Por ejemplo:  
  
    ```  
    cl /B1 file1.c  
    ```