---
title: "Type (Propiedad de acelerador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Type (propiedad)"
  - "VIRTKEY"
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Type (Propiedad de acelerador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La propiedad **Type** de un acelerador determina si la combinación de teclas de método abreviado asociada al identificador \(ID\) del acelerador es una combinación de teclas virtual o un valor de tecla ASCII\/ANSI:  
  
-   Si la propiedad **Type** es **ASCII**, el modificador \([Modifier](../windows/accelerator-modifier-property.md)\) sólo podrá ser "Ninguno" o "Alt" \(también podrá definirse un acelerador que utilice la tecla CTRL, en cuyo caso deberá anteponerse el prefijo ^ a la tecla en cuestión\).  
  
-   Si la propiedad **Type** es **VIRTKEY**, cualquier combinación de valores de Modifier y de Key será válida.  
  
    > [!NOTE]
    >  Si desea especificar un valor en la tabla de aceleradores que se considere como ASCII\/ANSI, bastará con que, en la entrada de la tabla, haga clic en Type y seleccione ASCII en la lista desplegable.  No obstante, si utiliza el comando **Tecla siguiente** \(menú **Edición**\) para especificar la tecla, deberá cambiar la propiedad **Type** de VIRTKEY a ASCII *antes* de escribir el código de tecla \(Key\).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)