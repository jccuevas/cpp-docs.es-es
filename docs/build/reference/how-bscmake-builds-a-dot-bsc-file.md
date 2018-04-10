---
title: Cómo compila BSCMAKE un. Archivo BSC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb8e03bed85a5e466a3c41f0cffc51d35c4b4561
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-bscmake-builds-a-bsc-file"></a>Cómo compila BSCMAKE un archivo .Bsc
BSCMAKE genera o vuelve a generar un archivo .bsc de la manera más eficaz que puede. Para evitar posibles problemas, es importante comprender el proceso de compilación.  
  
 Cuando BSCMAKE genera un archivo de información de examen, trunca los archivos .sbr a longitud cero. Durante una compilación posterior del mismo archivo, un archivo .sbr de longitud cero (o vacío) indica a BSCMAKE que el archivo .sbr no tiene ninguna contribución nueva que aportar. Permite que BSCMAKE sabe que no es necesaria una actualización de la parte del archivo y una generación incremental será suficiente. En todas las generaciones (a menos que se especifica la opción/n), BSCMAKE intenta primero actualizar el archivo de forma incremental usando sólo los archivos .sbr que han cambiado.  
  
 BSCMAKE busca un archivo .bsc que tenga el nombre especificado con la opción/o. Si no se especifica/o, BSCMAKE busca un archivo que tiene el nombre base del primer archivo .sbr y una extensión de BSC. Si el archivo existe, BSCMAKE realiza una generación incremental del archivo de información de examen usando sólo los archivos .sbr participantes. Si el archivo no existe, BSCMAKE realiza una generación completa usando todos los archivos .sbr. Las reglas para las compilaciones son los siguientes:  
  
-   Para que una generación completa se realice correctamente, especificado todos los archivos .sbr deben existir y no se deben truncar. Si se trunca un archivo .sbr, se debe recompilar (por volver a compilar o ensamblar) antes de ejecutar BSCMAKE.  
  
-   Para que una generación incremental se realice correctamente, debe existir el archivo .bsc. Todos los archivos .sbr participantes, incluso los archivos vacíos, debe existir y debe especificarse en la línea de comandos BSCMAKE. Si se omite un archivo .sbr desde la línea de comandos, BSCMAKE quita su contribución del archivo.  
  
## <a name="see-also"></a>Vea también  
 [Crear un archivo .Bsc](../../build/reference/building-a-dot-bsc-file.md)