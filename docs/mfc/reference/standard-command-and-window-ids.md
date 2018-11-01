---
title: Identificadores de comandos y ventanas estándar
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 28279931c5d644ef333c03fd799c5f2fbf68ec52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647985"
---
# <a name="standard-command-and-window-ids"></a>Identificadores de comandos y ventanas estándar

La biblioteca Microsoft Foundation Class define una serie de comandos estándar y los identificadores de ventana en Afxres.h. Estos identificadores se usan con más frecuencia dentro de los editores de recursos y la ventana Propiedades para asignar mensajes a las funciones de controlador. Todos los comandos estándares tienen un **ID_** prefijo. Por ejemplo, cuando se usa el editor de menús, normalmente enlazar el elemento de menú Abrir archivo al identificador de comando ID_FILE_OPEN estándar.

Para la mayoría de los comandos, el código de aplicación no necesita hacer referencia al identificador de comando, ya que el marco de trabajo controla los comandos a través de mapas de mensajes en sus clases de marco principal (`CWinThread`, `CWinApp`, `CView`, `CDocument`, y así sucesivamente).

Además de los identificadores de comando estándar, se define un número de otros identificadores estándar que tienen un prefijo de **AFX_ID**. Estos identificadores incluyen los identificadores de ventana estándar (prefijo **AFX_IDW_**), los identificadores de cadena (prefijo **AFX_IDS_**) y otros tipos.

Los identificadores que comienzan por la **AFX_ID** prefijo rara vez se usan los programadores, pero es posible que deba hacer referencia a estos identificadores al reemplazar las funciones de framework que también hacen referencia a la **AFX_ID**s.

Los identificadores no se documentan individualmente en esta referencia. Puede encontrar más información sobre ellos en las notas técnicas [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), y [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
>  El archivo de encabezado Afxres.h indirectamente se incluye en Afxwin.h. Debe incluir explícitamente la instrucción siguiente en el archivo de script (.rc) de recursos de la aplicación:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
