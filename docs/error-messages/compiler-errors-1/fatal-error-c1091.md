---
title: Error irrecuperable C1091 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e9d5e9ba75457d89223ab187c1249cc73419fab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1091"></a>Error irrecuperable C1091
límite del compilador: la longitud de la cadena supera los bytes de 'length'.  
  
 Una constante de cadena supera el límite actual de la longitud de las cadenas.  
  
 Puede dividir la cadena estática en dos (o más) variables y usar [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) para unir el resultado como parte de la declaración o durante el tiempo de ejecución.