---
title: Formato de imagen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 356480333a62d998213726016f3940b318c218a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367945"
---
# <a name="image-format"></a>Formato de imágenes
El formato de imagen ejecutable es PE32 +. Imágenes ejecutables (archivos DLL y exe) están restringidas a un tamaño máximo de 2 gigabytes, para que direcciones relativas con un desplazamiento de 32 bits se puedan utilizar para tratar datos de imagen estática. Estos datos incluyen la tabla de direcciones de importación, constantes de cadena, datos globales estáticos y así sucesivamente.  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)