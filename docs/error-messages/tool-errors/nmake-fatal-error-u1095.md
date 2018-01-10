---
title: Error grave de NMAKE U1095 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1095
dev_langs: C++
helpviewer_keywords: U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 81d93635c50b304a5a2df027691470093d23bdbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1095"></a>Error grave de NMAKE U1095
línea de comandos expandida 'commandline' es demasiado largo  
  
 Después de la expansión de macro, la línea de comandos especificada supera el límite de longitud de líneas de comandos para el sistema operativo.  
  
 MS-DOS permite hasta 128 caracteres en una línea de comandos.  
  
 Si el comando es para un programa que puede aceptar la entrada de línea de comandos desde un archivo, cambie el comando y proporcione la entrada desde un archivo de disco o un archivo en línea. Por ejemplo, LINK y LIB aceptan la entrada desde un archivo de respuesta.