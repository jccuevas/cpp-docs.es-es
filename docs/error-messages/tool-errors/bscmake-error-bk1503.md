---
title: Error de BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: e0f05b3979024cb053394c51fa9337197b5de7bf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197865"
---
# <a name="bscmake-error-bk1503"></a>Error de BSCMAKE BK1503

no se puede escribir en el archivo ' nombredearchivo ' [: razón]

BSCMAKE combina los archivos. SBR generados durante la compilación en una base de datos de explorador. Si la base de datos del explorador resultante supera los 64 MB o si el número de archivos de entrada (. SBR) es superior a 4092, se emitirá este error.

Si el problema se debe a más de 4092 archivos. SBR, debe reducir el número de archivos de entrada. En Visual Studio, puede hacerlo mediante [/fr](../../build/reference/fr-fr-create-dot-sbr-file.md) todo el proyecto y, a continuación, volver a comprobar un archivo por archivo.

Si el problema se debe a un archivo. BSC mayor que 64 MB, si se reduce el número de archivos. SBR como entrada, se reducirá el tamaño del archivo. BSC resultante. Además, la cantidad de información de examen puede reducirse mediante el uso de/EM (excluir símbolos expandidos de macro),/el (excluir variables locales) y/es (excluir archivos del sistema).

## <a name="see-also"></a>Consulte también

[Opciones de BSCMAKE](../../build/reference/bscmake-options.md)
