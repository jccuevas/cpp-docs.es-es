---
title: Las herramientas del vinculador LNK2008 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4ee6a8a4c4cc6d33f47d5335daa9fccd4e5fd99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2008"></a>Error de las herramientas del vinculador LNK2008
Destino de la corrección no está alineado 'symbol_name'  
  
 LINK encontró un destino de la corrección en el archivo de objeto que no se ha alineado correctamente.  
  
 Este error puede deberse a personalizado producirlo una alineación de (por ejemplo, #pragma [pack](../../preprocessor/pack.md)), [alinear](../../cpp/align-cpp.md) modificador, o bien mediante código de lenguaje ensamblador que modifica la alineación.  
  
 Si el código no utiliza ninguno de los pasos anteriores, esto puede deberse al compilador.