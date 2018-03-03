---
title: Formato de imagen | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0761acfe02b7d86f9316d06913de15347e9d522
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="image-format"></a>Formato de imágenes
El formato de imagen ejecutable es PE32 +. Imágenes ejecutables (archivos DLL y exe) están restringidas a un tamaño máximo de 2 gigabytes, para que direcciones relativas con un desplazamiento de 32 bits se puedan utilizar para tratar datos de imagen estática. Estos datos incluyen la tabla de direcciones de importación, constantes de cadena, datos globales estáticos y así sucesivamente.  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)