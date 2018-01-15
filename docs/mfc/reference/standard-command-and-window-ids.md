---
title: "Comandos estándar e identificadores de ventana | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c8195b1ab967a0d6692e839b1db1e89ee6694d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
