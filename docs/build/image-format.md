---
title: Formato de imágenes
ms.date: 11/04/2016
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
ms.openlocfilehash: 71456af35960114ab64b076ebb9c0f9102613744
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509946"
---
# <a name="image-format"></a>Formato de imágenes

El formato de imagen ejecutable es PE32 +. Imágenes ejecutables (archivos DLL y exe) están restringidas a un tamaño máximo de 2 gigabytes, por lo que las direcciones relativas con un desplazamiento de 32 bits pueden usarse para datos de imagen estática de direcciones. Estos datos incluyen la tabla de importar direcciones, las constantes de cadena, datos globales estáticos y así sucesivamente.

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)