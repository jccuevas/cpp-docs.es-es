---
title: Comandos estándar e identificadores de ventana | Documentos de Microsoft
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
ms.openlocfilehash: 72b50108a9b880961f0dd8bcded1126a635fb9e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="standard-command-and-window-ids"></a>Identificadores de comandos y ventanas estándar
La biblioteca Microsoft Foundation Class define una serie de comandos estándar y los identificadores de ventana en Afxres.h. Estos identificadores se usan normalmente en los editores de recursos y la ventana Propiedades para asignar mensajes a las funciones de controlador. Todos los comandos estándares tienen un **ID_** prefijo. Por ejemplo, cuando se utiliza el editor de menús, normalmente enlaza el elemento de menú Abrir archivo para el estándar `ID_FILE_OPEN` identificador de comando.  
  
 Para la mayoría de los comandos, código de aplicación no necesita hacer referencia al identificador de comando, puesto que el marco de trabajo controla los comandos a través de mapas de mensajes en sus clases de framework principal ( `CWinThread`, `CWinApp`, < c4 > `CView` , **CDocument**, y así sucesivamente).  
  
 Además de los identificadores de comando estándar, un número de otros identificadores estándar se define que tienen un prefijo de **AFX_ID**. Estos identificadores son identificadores de ventana estándar (prefijo **AFX_IDW_**), identificadores de cadena (prefijo **AFX_IDS_**) y algunos otros tipos.  
  
 Id. que comienzan por la **AFX_ID** prefijo rara vez se utilizan por los programadores, pero tendrá que hacer referencia a estos identificadores al reemplazar las funciones de framework que también hacen referencia a la **AFX_ID**s.  
  
 Id. no se documenta individualmente en esta referencia. Puede encontrar más información sobre ellos en notas técnicas [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), y [22](../../mfc/tn022-standard-commands-implementation.md).  
  
> [!NOTE]
>  El archivo de encabezado Afxres.h indirectamente se incluye en Afxwin.h. Debe incluir explícitamente la instrucción siguiente en el archivo de script (.rc) de recursos de la aplicación:  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
