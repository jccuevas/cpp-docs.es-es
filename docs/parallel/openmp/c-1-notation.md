---
title: "C.1 notación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9772b2a4b27521c7aa256f9ee7760a4687152b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c1-notation"></a>C.1 Notación
Las reglas de gramática consisten en el nombre de un no terminal, seguido por un signo de dos puntos seguido de alternativas de reemplazo en líneas independientes.  
  
 La expresión sintáctica termopt indica que el término es opcional en la sustitución.  
  
 La expresión sintáctica *término*optseq es equivalente a *término-seq*opt, con las siguientes reglas adicionales:  
  
 *término-seq* :  
  
 *término*  
  
 *término-seq término*  
  
 *término-seq* , *término*