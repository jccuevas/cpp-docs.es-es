---
title: Error grave de NMAKE U1095 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13c819d18149e61bca71f6a4cb10ea851a2d485d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1095"></a>Error grave de NMAKE U1095
línea de comandos expandida 'commandline' es demasiado largo  
  
 Después de la expansión de macro, la línea de comandos especificada supera el límite de longitud de líneas de comandos para el sistema operativo.  
  
 MS-DOS permite hasta 128 caracteres en una línea de comandos.  
  
 Si el comando es para un programa que puede aceptar la entrada de línea de comandos desde un archivo, cambie el comando y proporcione la entrada desde un archivo de disco o un archivo en línea. Por ejemplo, LINK y LIB aceptan la entrada desde un archivo de respuesta.