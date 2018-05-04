---
title: -BIND | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bind
dev_langs:
- C++
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b77c778017dc78235948e8d23db136c1f63ab12d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="bind"></a>/BIND
```  
/BIND[:PATH=path]  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción establece las direcciones de los puntos de entrada en la tabla de direcciones de importación para un archivo ejecutable o DLL. Utilice esta opción para reducir el tiempo de carga de un programa.  
  
 Especifique del programa archivo ejecutable y los archivos DLL en el *archivos* argumento en la línea de comandos EDITBIN. Opcional *ruta de acceso* argumento /BIND especifica la ubicación de los archivos DLL que se utilizan en los archivos especificados. Separe varios directorios con un punto y coma (**;**). Si *ruta de acceso* no se especifica, EDITBIN buscará en los directorios especificados en la variable de entorno PATH. Si *ruta de acceso* se especifica, EDITBIN pasará por alto la variable PATH.  
  
 De forma predeterminada, el cargador del programa establece las direcciones de puntos de entrada cuando cargue un programa. La cantidad de tiempo que este proceso tarda varía, dependiendo del número de archivos DLL y el número de puntos de entrada que se hace referencia en el programa. Si se ha modificado un programa con la opción /BIND y si las direcciones base del archivo ejecutable y sus archivos DLL no entren en conflicto con los archivos DLL que ya están cargadas, el sistema operativo no es necesario establecer estas direcciones. En una situación donde los archivos se basan incorrectamente, el sistema operativo vuelve a colocar los archivos DLL y vuelve a calcular las direcciones de punto de entrada, que agrega al tiempo de carga del programa.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)