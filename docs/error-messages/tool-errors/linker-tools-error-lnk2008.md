---
title: Las herramientas del vinculador LNK2008 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7c2fecff55677653c25c7d87fb22fa984526159
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2008"></a>Error de las herramientas del vinculador LNK2008
Destino de la corrección no está alineado 'symbol_name'  
  
 LINK encontró un destino de la corrección en el archivo de objeto que no se ha alineado correctamente.  
  
 Este error puede deberse a personalizado producirlo una alineación de (por ejemplo, #pragma [pack](../../preprocessor/pack.md)), [alinear](../../cpp/align-cpp.md) modificador, o bien mediante código de lenguaje ensamblador que modifica la alineación.  
  
 Si el código no utiliza ninguno de los pasos anteriores, esto puede deberse al compilador.