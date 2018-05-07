---
title: Error irrecuperable C1047 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce88321173ee2c8cc286f18d8ab8f1bf5ec98e13
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1047"></a>Error irrecuperable C1047
El objeto o el archivo de biblioteca 'file' se creó con un compilador anterior a otros objetos; recompile las bibliotecas y los objetos antiguos.  
  
 El error C1047 se produce cuando los archivos o bibliotecas de objeto compilados con **/LTCG** están vinculados entre sí, pero donde se crean esos archivos o bibliotecas de objetos con versiones diferentes del conjunto de herramientas de Visual C++.  
  
 Esto puede suceder si empieza a usar una nueva versión del compilador pero no realiza una recompilación limpia de las bibliotecas o los archivos de objetos existentes.  
  
 Para resolver el error C1047, recompile todos los archivos y bibliotecas de objetos.