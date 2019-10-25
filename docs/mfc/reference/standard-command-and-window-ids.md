---
title: Identificadores de comandos y ventanas estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 40783bc19e51afb0e9fe9e4a429df0239a8e7f09
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907716"
---
# <a name="standard-command-and-window-ids"></a>Identificadores de comandos y ventanas estándar

El biblioteca MFC define un número de identificadores de comandos y ventanas estándar en AFXRES. h. Estos identificadores se usan normalmente en los editores de recursos y el [Asistente para clases](mfc-class-wizard.md) para asignar mensajes a las funciones de controlador. Todos los comandos estándar tienen un prefijo **ID_** . Por ejemplo, cuando se usa el editor de menús, normalmente se enlaza el elemento de menú archivo abierto al identificador de comando estándar de ID_FILE_OPEN.

Para la mayoría de los comandos estándar, el código de aplicación no necesita hacer referencia al identificador de comando, porque el propio marco de trabajo controla los comandos a través de`CWinThread`mapas de `CView`mensajes en sus clases de marco de trabajo principales (, `CWinApp`,, `CDocument`y así sucesivamente).

Además de los identificadores de comando estándar, se definen varios identificadores estándar que tienen un prefijo de **AFX_ID**. Estos identificadores incluyen los identificadores de ventana estándar (prefijo **AFX_IDW_** ), los identificadores de cadena (prefijo **AFX_IDS_** ) y otros tipos.

Los programadores raramente usan los identificadores que comienzan con el prefijo **AFX_ID** , pero es posible que tenga que hacer referencia a estos identificadores al reemplazar las funciones de marco de trabajo que también hacen referencia a **AFX_ID**s.

Los identificadores no se documentan individualmente en esta referencia. Puede encontrar más información sobre ellos en las notas técnicas [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md)y [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
>  El archivo de encabezado AFXRES. h se incluye indirectamente en AFXWIN. h. Debe incluir explícitamente la siguiente instrucción en el archivo de script de recursos (. RC) de la aplicación:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Vea también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
