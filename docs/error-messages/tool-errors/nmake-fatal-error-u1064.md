---
title: Error grave de NMAKE U1064 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1064
dev_langs: C++
helpviewer_keywords: U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 20b6c767145176c459d0b70d96842223218cd0b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1064"></a>Error grave de NMAKE U1064
Archivo MAKE no se encuentra y se especificó ningún destino  
  
 La línea de comandos NMAKE no ha especificado un archivo MAKE o un destino y el directorio actual no contiene un archivo denominado MAKE.  
  
 NMAKE requiere un archivo MAKE o un destino de línea de comandos (o ambos). Para poner a disposición de NMAKE un archivo MAKE, especifique la opción/f o bien coloque un archivo denominado MAKE en el directorio actual. NMAKE puede crear un destino de línea de comandos mediante una regla de inferencia si no se proporciona un archivo MAKE.