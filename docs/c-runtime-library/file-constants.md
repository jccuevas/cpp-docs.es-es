---
title: Constantes de archivo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
dev_langs: C++
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59e108f8674b002cdbc5e7ab0b9c1868eea632df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="file-constants"></a>Constantes de archivo
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 La expresión de entero formada a partir de una o varias de estas constantes determina el tipo de operaciones de lectura o escritura permitidas. Se forma mediante la combinación de una o varias constantes con una constante de modo de traducción.  
  
 Las constantes de archivo son las siguientes:  
  
 `_O_APPEND`  
 Recoloca el puntero de archivo al final del archivo antes de cada operación de escritura.  
  
 `_O_CREAT`  
 Crea y abre un nuevo archivo para escritura; esto no tiene ningún efecto si el archivo especificado por *filename* existe.  
  
 `_O_EXCL`  
 Devuelve un valor de error si el archivo especificado por *filename* existe. Solo se aplica cuando se usa con `_O_CREAT`.  
  
 `_O_RDONLY`  
 Abre el archivo solo para lectura; si se especifica esta marca, no se pueden proporcionar `_O_RDWR` ni `_O_WRONLY`.  
  
 `_O_RDWR`  
 Abre el archivo para lectura y escritura; si se especifica esta marca, no se pueden proporcionar `_O_RDONLY` ni `_O_WRONLY`.  
  
 `_O_TRUNC`  
 Abre un archivo existente y lo trunca a longitud cero. El archivo debe tener permiso de escritura. Se destruye el contenido del archivo. Si se proporciona esta marca, no se puede especificar `_O_RDONLY`.  
  
 `_O_WRONLY`  
 Abre el archivo solo para escritura; si se especifica esta marca, no se pueden proporcionar `_O_RDONLY` ni `_O_RDWR`.  
  
## <a name="see-also"></a>Vea también  
 [_open, _wopen](../c-runtime-library/reference/open-wopen.md)   
 [_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)