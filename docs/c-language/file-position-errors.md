---
title: "Errores de posición de archivo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc55622f724a903c94fe49a935b906d2826297ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="file-position-errors"></a>Errores de posición de archivo
**ANSI 4.9.9.1, 4.9.9.4** Valor en el que establecen la macro `errno` las funciones `fgetpos` o `ftell` cuando se produce un error  
  
 Cuando `fgetpos` o `ftell` producen un error, `errno` es establece en la constante de manifiesto `EINVAL` si la posición no es válida o EBADF si el número de archivo es incorrecto. Las constantes se definen en ERRNO.H.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)