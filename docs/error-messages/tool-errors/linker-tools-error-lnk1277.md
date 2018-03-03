---
title: Las herramientas del vinculador LNK1277 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3606207afc197dc26ac0540d476b74f52c0dc0a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1277"></a>Error de las herramientas del vinculador LNK1277
registro de objeto no encontrado en pgd (nombre de archivo)  
  
 Cuando se usa [PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), la ruta de acceso de uno de los archivos .lib, def o .obj entrados era diferente de la ruta de acceso en el que se encontraron durante/LTCG: PGINSTRUMENT. Esto podría deberse a un cambio en la variable de entorno LIB después de/LTCG: PGINSTRUMENT. La ruta de acceso completa a los archivos de entrada se almacena en el archivo. pgd.  
  
 / LTCG: PGOPTIMIZE requiere que las entradas sean idénticas a la fase/LTCG: PGINSTRUMENT.  
  
 Para resolver esta advertencia, realice una de las siguientes acciones:  
  
-   Ejecute/LTCG: PGINSTRUMENT, vuelva a realizar todas las ejecuciones de prueba y/LTCG: PGOPTIMIZE.  
  
-   Cambie la variable de entorno LIB al que tenía cuando se ejecutó/LTCG: PGINSTRUMENT.  
  
 No se recomienda evitar LNK1277 utilizando/LTCG: PGUPDATE.