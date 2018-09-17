---
title: Formato de imagen | Microsoft Docs
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
ms.openlocfilehash: 0e69d1a7c62d4e9c52cc628f30f94c346d83647f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715421"
---
# <a name="image-format"></a>Formato de imágenes

El formato de imagen ejecutable es PE32 +. Imágenes ejecutables (archivos DLL y exe) están restringidas a un tamaño máximo de 2 gigabytes, por lo que las direcciones relativas con un desplazamiento de 32 bits pueden usarse para datos de imagen estática de direcciones. Estos datos incluyen la tabla de importar direcciones, las constantes de cadena, datos globales estáticos y así sucesivamente.

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)