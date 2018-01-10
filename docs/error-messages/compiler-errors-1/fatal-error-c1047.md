---
title: Error irrecuperable C1047 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1047
dev_langs: C++
helpviewer_keywords: C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ddc117d1e83c635bfbc644606c6c8c6032ff4f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1047"></a>Error irrecuperable C1047
El objeto o el archivo de biblioteca 'file' se creó con un compilador anterior a otros objetos; recompile las bibliotecas y los objetos antiguos.  
  
 El error C1047 se produce cuando los archivos o bibliotecas de objeto compilados con **/LTCG** están vinculados entre sí, pero donde se crean esos archivos o bibliotecas de objetos con versiones diferentes del conjunto de herramientas de Visual C++.  
  
 Esto puede suceder si empieza a usar una nueva versión del compilador pero no realiza una recompilación limpia de las bibliotecas o los archivos de objetos existentes.  
  
 Para resolver el error C1047, recompile todos los archivos y bibliotecas de objetos.