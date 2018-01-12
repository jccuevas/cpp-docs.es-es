---
title: Error grave de NMAKE U1073 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1073
dev_langs: C++
helpviewer_keywords: U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: faae317df44560991a88d47ec7f123e6a8126429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1073"></a>Error grave de NMAKE U1073
no sabe cómo hacer 'nombrededestino'  
  
 El destino especificado no existe y no hay ningún comando para ejecutar o que se aplique la regla de inferencia.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Compruebe la ortografía del nombre de destino.  
  
2.  Si *targetname* es un pseudodestino, especifíquelo como un destino en otro bloque de descripción.  
  
3.  Si *targetname* es una llamada de macro, asegúrese de que no se expande a una cadena nula.