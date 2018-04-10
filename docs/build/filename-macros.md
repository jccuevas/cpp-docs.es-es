---
title: Macros de nombre de archivo | Documentos de Microsoft
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
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2073e4fcb365b3beb10d4040c0f54d9f61a0431
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="filename-macros"></a>Macros de nombre de archivo
Las macros de nombre de archivo están predefinidas como nombres de archivo especificados en la dependencia (especificaciones de nombre de archivo no completa en el disco). Estas macros no tienen que incluirse entre paréntesis cuando se invoca; Especifique solo un $ tal como se muestra.  
  
|Macro|Significado|  
|-----------|-------------|  
|**$@**|Nombre del destino actual completa (ruta de acceso, nombre base, extensión), como se especifica actualmente.|  
|**$$@**|Nombre del destino actual completa (ruta de acceso, nombre base, extensión), como se especifica actualmente. Válido solo como una dependencia en una dependencia.|  
|**$\***|Nombre del destino actual ruta de acceso y base sin extensión de archivo.|  
|**$\*\***|Todos los dependientes del destino actual.|  
|**$?**|Todos los dependientes con una marca de tiempo posterior que el destino actual.|  
|**$<**|Archivo dependiente con una marca de tiempo posterior que el destino actual. Válido únicamente en comandos en reglas de inferencia.|  
  
 Para especificar parte de una macro de nombre de archivo predefinido, anexe un modificador de macro y entre paréntesis la macro modificada.  
  
|Modificador|Parte de nombre de archivo resultante|  
|--------------|-----------------------------|  
|**D**|Unidad más directorio|  
|**B**|Nombre base|  
|**F**|Nombre base más extensión|  
|**R**|Unidad más directorio más nombre base|  
  
## <a name="see-also"></a>Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)