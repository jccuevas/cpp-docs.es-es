---
title: Comandos estándar y los identificadores de ventana | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2106312bd83edc4a37c904e2ee87ce78acb82904
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379136"
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
