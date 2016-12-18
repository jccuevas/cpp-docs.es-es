---
title: "Identificadores de comandos y ventanas est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "identificadores de comandos y ventanas estándar"
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: 13
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Identificadores de comandos y ventanas est&#225;ndar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La biblioteca Microsoft Foundation Class define varios id. de comando estándar y de la ventana en Afxres.h.  Estos id. se utilizan con más frecuencia en los editores de recursos y la ventana Propiedades para asignar mensajes al controlador trabaja.  Todos los comandos estándar tienen un prefijo de **ID\_** .  Por ejemplo, cuando se utiliza el editor de menús, enlace normalmente el elemento de menú para Abrir archivos a la identificación estándar de comando de `ID_FILE_OPEN`  
  
 Para la mayoría de los comandos estándar, el código de aplicación no necesita hacer referencia al identificador de comando, porque el marco propia controla los comandos a través de mapas de mensajes en las clases principales del marco \(`CWinThread`, `CWinApp`, `CView`, **CDocument**, etc.\).  
  
 Además de id. de comando estándar, se definen varios otros id. estándar que tienen un prefijo de **AFX\_ID**.  Estos id. incluyen los id. estándar de la ventana \(prefijo **AFX\_IDW\_**\), los id. de la cadena \(prefijo **AFX\_IDS\_**\), y otros tipos.  
  
 Los id. que comienzan con el prefijo de **AFX\_ID** se utilizan raramente por los desarrolladores, pero quizá sea necesario hacer referencia a estos id. al reemplazar el marco funcionan que también hacen referencia a s para **AFX\_ID**.  
  
 Los id. no se documentan individualmente en esta referencia.  Puede encontrar más información en ellos en las notas técnicas [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), y [22](../../mfc/tn022-standard-commands-implementation.md).  
  
> [!NOTE]
>  El archivo de encabezado Afxres.h se incluye indirectamente en Afxwin.h.  Debe incluir explícitamente la instrucción siguiente en el archivo de script de recursos de la aplicación \(.rc\):  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/CPP/standard-command-and-window-ids_1.h)]  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)