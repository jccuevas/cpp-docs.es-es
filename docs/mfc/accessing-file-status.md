---
title: Acceso al estado del archivo
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: 3e16f8b11d17cd911646c3c9206d1d7deb577ef9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629793"
---
# <a name="accessing-file-status"></a>Acceso al estado del archivo

`CFile` También permite obtener estado de archivo, incluso si el archivo existe, fecha de creación y modificación, horas, tamaño lógico y ruta de acceso.

### <a name="to-get-file-status"></a>Para obtener el estado de archivo

1. Use la [CFile](../mfc/reference/cfile-class.md) clase para obtener y establecer información acerca de un archivo. Una aplicación útil consiste en usar el `CFile` función miembro estática **GetStatus** para determinar si existe un archivo. **GetStatus** devuelve 0 si el archivo especificado no existe.

Por lo tanto, podría usar el resultado de **GetStatus** para determinar si se debe usar el **CFile:: modeCreate** marca al abrir un archivo, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Para obtener información relacionada, consulte [serialización](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Vea también

[Archivos](../mfc/files-in-mfc.md)

