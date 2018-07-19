---
title: C.1 notación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39e8610524e20aa99ea316d62f36b512700e377e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686820"
---
# <a name="c1-notation"></a>C.1 Notación
Las reglas de gramática consisten en el nombre de un no terminal, seguido por un signo de dos puntos seguido de alternativas de reemplazo en líneas independientes.  
  
 La expresión sintáctica termopt indica que el término es opcional en la sustitución.  
  
 La expresión sintáctica *término*optseq es equivalente a *término-seq*opt, con las siguientes reglas adicionales:  
  
 *término-seq* :  
  
 *Término*  
  
 *término-seq término*  
  
 *término-seq* , *término*