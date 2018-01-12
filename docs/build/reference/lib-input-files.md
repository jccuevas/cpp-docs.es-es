---
title: Archivos de entrada de LIB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Lib
dev_langs: C++
helpviewer_keywords: input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5fea7a8700eb2f5a5deee7afd05af8b0de0e4e71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="lib-input-files"></a>Archivos de entrada de LIB
Los archivos de entrada que espera LIB dependen del modo en que se esté utilizando, como se muestra en la tabla siguiente.  
  
|Modo|Entrada|  
|----------|-----------|  
|Predeterminado (generar o modificar una biblioteca)|COFF (archivos) objeto (.obj), bibliotecas COFF (.lib), archivos de objeto (.obj) del formato de modelo de objeto (OMF) de 32 bits|  
|Extraer a un miembro con/Extract|Biblioteca COFF (.lib)|  
|Creación de una exportación de archivos e importar la biblioteca con/def|Archivo de definición de módulos (.def), archivos objeto (.obj) COFF, bibliotecas COFF (.lib), archivos de objeto (.obj) OMF de 32 bits|  
  
> [!NOTE]
>  Bibliotecas OMF creadas con la versión de 16 bits de LIB no se puede usar como entrada para la versión de 32 bits de LIB.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre LIB](../../build/reference/overview-of-lib.md)