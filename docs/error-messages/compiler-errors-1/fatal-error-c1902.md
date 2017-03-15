---
title: Error grave C1902 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: b551b1a7e0ae03a7de5108a1d114155786972847
ms.openlocfilehash: 79987719614dfa3075f9a9090ca1d97f6546ceb3
ms.lasthandoff: 02/24/2017

---
# <a name="fatal-error-c1902"></a>Error irrecuperable C1902
Error de coincidencia de administrador de base de datos de programa; Compruebe la instalación  
  
Un archivo de base de datos de programa (.pdb) se creó con una versión más reciente de mspdb*XXX*dll a la que el compilador ha encontrado en el sistema. Este error suele indicar que mspdbsrv.exe o mspdbcore.dll faltan o versiones distintas de mspdb*XXX*.dll. (El *XXX* marcador de posición en el mspdb*XXX*cambios de nombre de archivo .dll con cada versión del producto. Por ejemplo, en Visual Studio 2015, el nombre de archivo es mspdb140.dll).  
  
Asegúrese de versiones coincidentes de mspdbsrv.exe, mspdbcore.dll y mspdb*XXX*.dll están instalados en su sistema. Asegúrese de que las versiones no coinciden no se han copiado en el directorio que contiene las herramientas del compilador y el vínculo para la plataforma de destino. Por ejemplo, es posible que haya copiado los archivos para poder invocar la herramienta de compilador o un vínculo desde el símbolo del sistema sin establecer el **ruta de acceso** variable de entorno en consecuencia.
