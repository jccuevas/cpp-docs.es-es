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
ms.openlocfilehash: 23c626940e700d3e9827ef6a7cf849d970e40d5d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619785"
---
# <a name="accessing-file-status"></a>Acceso al estado del archivo

`CFile`también admite la obtención del estado del archivo, incluso si el archivo existe, las fechas y horas de creación y modificación, el tamaño lógico y la ruta de acceso.

### <a name="to-get-file-status"></a>Para obtener el estado del archivo

1. Use la clase [CFile](reference/cfile-class.md) para obtener y establecer información sobre un archivo. Una aplicación útil es usar la `CFile` función miembro estática **getStatus** para determinar si existe un archivo. **GetStatus** devuelve 0 si el archivo especificado no existe.

Por lo tanto, puede usar el resultado de **getStatus** para determinar si se va a usar la marca **CFile:: modeCreate** al abrir un archivo, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Para obtener información relacionada, vea [serialización](serialization-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Archivos](files-in-mfc.md)
