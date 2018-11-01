---
title: Error de BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: 2c8ca005922c3c94b557e2f1052e8811099d9948
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555813"
---
# <a name="bscmake-error-bk1503"></a>Error de BSCMAKE BK1503

no se puede escribir en el archivo 'filename' [: motivo]

BSCMAKE combina los archivos .sbr generados durante la compilación en una base de datos del explorador. Si la base de datos del explorador resultante supera los 64 MB, o si el número de archivos de entrada (.sbr) supera los 4092, se emitirá este error.

Si hay más de 4092 archivos .sbr causa el problema, se debe reducir el número de archivos de entrada. Desde dentro de Visual Studio, esto puede realizarse por [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) el proyecto completo, a continuación, volver a comprobar en el archivo por archivo.

Si el problema se debe a un archivo .bsc más de 64MB, lo que reduce el número de archivos .sbr como entrada se reducirá el tamaño del archivo .bsc resultante. Además, se puede reducir la cantidad de información de examen mediante el uso de los /Em (excluir símbolos de expandidos de Macro), /El (excluir Variables locales) y/es (excluir archivos del sistema).

## <a name="see-also"></a>Vea también

[Opciones de BSCMAKE](../../build/reference/bscmake-options.md)