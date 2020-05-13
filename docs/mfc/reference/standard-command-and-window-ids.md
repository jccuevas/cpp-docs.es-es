---
title: Identificadores de comandos y ventanas estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: a7f9e37702c686e13379d4034be94949f92e5e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372957"
---
# <a name="standard-command-and-window-ids"></a>Identificadores de comandos y ventanas estándar

La biblioteca Microsoft Foundation Class define una serie de datos de comandos y ventanas estándar en Afxres.h. Estos identificadores se usan con mayor frecuencia en los editores de recursos y el [Asistente para](mfc-class-wizard.md) clases para asignar mensajes a las funciones de controlador. Todos los comandos estándar tienen un prefijo **ID_.** Por ejemplo, cuando se utiliza el editor de menús, normalmente se enlaza el elemento de menú Abrir archivo al identificador de comando estándar ID_FILE_OPEN.

Para la mayoría de los comandos estándar, el código de aplicación no necesita hacer referencia al`CWinThread` `CWinApp`identificador `CView` `CDocument`de comando, porque el propio marco de trabajo controla los comandos a través de mapas de mensajes en sus clases de marco de trabajo principal ( , , , , , etc.).

Además de los argumentos de comando estándar, se definen varios otros iDs estándar que tienen un prefijo de **AFX_ID**. Estos iDs incluyen los iDs de ventana estándar **(prefijo AFX_IDW_),** los ides de cadena **(prefijo AFX_IDS_)** y varios otros tipos.

Los id que comienzan con el prefijo **AFX_ID** rara vez son utilizados por los programadores, pero es posible que deba hacer referencia a estos ID al reemplazar funciones de marco de trabajo que también hacen referencia a la **AFX_ID**s.

Los ID no se documentan individualmente en esta referencia. Puede encontrar más información sobre ellos en Notas Técnicas [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md)y [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
> El archivo de encabezado Afxres.h se incluye indirectamente en Afxwin.h. Debe incluir explícitamente la siguiente instrucción en el archivo de script de recursos (.rc) de la aplicación:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
