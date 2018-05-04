---
title: Archivos de entrada de LIB | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 140a0f1d9ef6fdb3ca5e6d6977804684c88af1fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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